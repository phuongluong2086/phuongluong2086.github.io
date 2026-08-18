# phuongluong2086.github.io

GIS and remote sensing portfolio — Phuong Luong.
Built with [Quarto](https://quarto.org) and published with GitHub Pages.

Live site: <https://phuongluong2086.github.io/>

## Build

```bash
quarto render     # writes the site to docs/
quarto preview    # live-reloading local server
```

`docs/` is the published output and **is committed** — GitHub Pages serves it
from `main` → `/docs` (Settings → Pages → Deploy from a branch). Commit the
rendered `docs/` alongside every source change, or the live site will not move.

## Layout

| Path | What it is |
| --- | --- |
| `*.qmd` | Top-level pages (home, about, projects, skills, experience, contact) |
| `projects/*.qmd` | One case study per file; front matter feeds the project cards |
| `_includes/` | Nav, footer, `<head>` additions, and the two listing templates |
| `_drafts/` | Unfinished pages. The `_` prefix means Quarto does not render them |
| `styles.css` | The entire design system — `theme: none`, so no Bootstrap |
| `assets/` | Profile photo, favicon |

## Adding a project

Create `projects/my-project.qmd` with this front matter:

```yaml
---
title: "My Project"
description: "One line, shown on the project card."
project-type: "REMOTE SENSING · SENTINEL-2"
image-class: satellite     # satellite | spatial | webgis — see styles.css §6
order: 4                   # controls sort order and the 01/02/03 card number
---
```

Both the homepage grid and the projects page are generated from these files by
Quarto listings, so there is nothing to update by hand in `index.qmd` or
`projects.qmd`. For a new `image-class`, add a matching gradient in `styles.css`
under section 6.

## Notes for editing

- Navigation is hand-written in `_includes/nav.html`, not the Quarto navbar.
  With `theme: none` there is no Bootstrap, so the built-in navbar would not
  render at all.
- Use the `.band` class for full-width padded sections, **not** `.section` —
  Pandoc consumes `.section` on a fenced div to emit a bare `<section>` element
  and drops the class.
- The listing templates in `_includes/*.ejs` must emit a single unindented line.
  See the comments at the top of those files before changing them.
