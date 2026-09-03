# Ideaphylo

Phylogenetic trees of **ideas**, on a phone.

One self-contained `index.html`. No build step, no server, no dependencies, no network.
Open the file and it works; everything is stored in the browser.

## Why

An idea is rarely born from nothing. It is a copy of an earlier idea with something
changed — and most of those changes die. Ideaphylo lays a line of thinking out the way
a biologist lays out a clade: each node descends from the one above it, dead branches
are kept rather than deleted, and hybrids that came out of two lineages are marked as such.

Read a path from root to tip and you get the story of how a thought changed, and why.

## Use it

Open `index.html` in a browser. On a phone, *Share → Add to Home Screen* makes it launch
like an app, full screen and offline.

| | |
|---|---|
| **Tap** an idea | select it — what you type below becomes its descendant |
| **Tap again** | edit the text in place |
| **Long-press** | full action sheet |
| **Selected row's controls** | `← raise` a layer · `→ nest` under the idea above · `⇱ move` anywhere in the tree · `⋯` for everything else |
| **Swipe right / left** | re-parent: descend from the idea above / promote a level |
| **Tap the circle** | collapse or expand a branch (the number is what's hidden) |
| **Focus** | make any idea the temporary root — how deep trees stay readable on a small screen |
| **◱** | whole-tree overview; tap any node to jump to it |

The compose bar always shows what a new idea will attach to, and grows in three directions:

- **↳ under** — a descendant. Selection stays on the parent after each entry, so a burst of
  typing produces a fan of variants rather than a chain; dive in by tapping.
- **⇢ beside** — a sibling, alongside.
- **↰ above** — a new **ancestor**, inserted above, for when you realise a set of ideas
  descend from something you hadn't written down yet. Siblings share a parent by
  definition, so the new ancestor takes in *every* sibling — the toast offers
  **Just this one** if you only meant to wrap the one idea. Used on a root, it becomes the
  common ancestor of every root lineage.

Paste a whole indented outline into the bar (spaces or tabs) and it grows the entire
subtree at once.

## What a node carries

- **Text** — the idea.
- **Δ Change** — what this mutated *away from* its parent. The field that makes the tree
  a phylogeny rather than an outline.
- **Note** — evidence, caveats, sources. Collapsed to one line until the row is selected.
- **Status** — thriving ★, untested ⁇, dead end ✕. Dead ends are worth keeping: an extinct
  branch still records that the territory was explored.
- **⤳ Merge** — a second ancestor, for ideas born where two lineages met. Drawn as a dashed
  arc in the overview.

## Look

Strictly monochrome, light and dark — ink on paper, greys only, hairline rules, no
shadows or gradients. Hierarchy is carried by weight, indentation and inversion rather
than by colour, which is what lets it read the same on an e-ink screen as on an LCD.
Both themes are verified to contain no non-grey pixel.

## Keeping your work

Saved to `localStorage` automatically; nothing leaves the device. Reopening restores the
tree, the selected idea and the scroll position, so it picks up mid-thought.

**Your tree is meant to outlive the code.** The storage key never changes between
versions, the schema version travels inside the payload, and every load is rebuilt into a
valid forest before use — children are the structural truth, parents are re-derived,
duplicate claims and cycles are cut, unknown fields are defaulted, fields from a newer
build are ignored rather than fatal. A tree written by any past or future build opens.

If the stored data still can't be read, it is **never** overwritten: writes stop, the
bytes are left exactly as they are, and you are offered a restore point, a download of the
unreadable data, or a deliberate fresh start. Up to three **restore points** are kept —
one per six hours of use — under ☰ → *Restore a saved point*. The ☰ menu also shows what
is stored and when it was last saved.

Editing in two tabs is detected rather than silently clobbered.

One caveat worth knowing: `localStorage` is scoped to the origin the page is served from.
Opening the same file from a different origin — a web host instead of `file://`, or another
device — starts an empty tree. Carry it across with **Export as JSON** → **Import JSON
file**; that path is lossless.

- **JSON** export/import — lossless, the format to trust for backups.
- **Markdown** export — a plain indented outline that also round-trips back in through
  *Import outline*, statuses, Δ-lines and notes included.

Both are in the ☰ menu, and both copy to the clipboard with a download as a fallback.

## Rearranging

A selected idea carries its own controls, so nothing is hidden behind a gesture you have
to know about:

- **← raise** — the whole clade moves up a layer, descendants and all.
- **→ nest** — it descends from the idea above instead.
- **⇱ move** — then tap any destination: the clade moves there whole. Tap *Make root* to
  cut it loose as its own lineage.
- **⎘ copy** — the same flow, switched at the top bar (or ⋯ → *Copy into…*). The
  destination clade **inherits a copy** of the whole clade; the original stays put. The
  graft is tagged **⤳** with where it was inherited from, and evolves independently
  afterwards — edit one and the other is untouched. Tap *Unlink source* on the toast if
  you would rather not record the provenance, or *As new lineage* to graft it as its own
  root instead.
- **⋯ → Dissolve** — deletes one idea and raises its children into its place. The inverse
  of **↰ above**, for when an intermediate idea turns out to be doing no work.

Swiping a row right or left does *nest* and *raise* too, once you know it's there.

`⌘Z` undoes; every destructive action offers an undo.

## On a keyboard

`↑`/`↓` move the selection · `←`/`→` collapse and expand · `Enter` edits ·
`Tab` / `⇧Tab` re-parent · `⌘Z` / `⇧⌘Z` undo and redo · `Esc` backs out.
