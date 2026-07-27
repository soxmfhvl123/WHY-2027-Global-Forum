# WHY : 2027 — Global Forum for Knowledge & Design

Website prototype for the WHY Global Forum, themed *Humanity : Love & Excellence*.
January 2027, Hyundai Motor Group Yangjae Headquarters, Seoul.

## Contents

| Path | What it is |
|---|---|
| `index.html` | The whole site — a single self-contained file (markup, styles, and the 3D hero) |
| `logos/` | Partner marks, plus the untouched source files they were made from |

Open `index.html` in a browser. No build step and no dependencies to install;
Three.js and Inter load from a CDN at runtime.

## The hero

The field is roughly a thousand instanced spheres running a small physics loop:
a weak pull toward the centre, soft repulsion so the balls hold a gap rather than
packing solid, and hard contact resolution. The pull is anisotropic and equal on X
and Z, which shapes the field into a flat **disc** — spinning it on the Y axis
therefore never empties the left and right edges.

- **Drag** to rotate, with inertia.
- **Click** to scatter the balls out from that point; they settle back on their own.
- Desktop opens on a slight tilt, phones on a steeper top-down angle where the
  disc's circular face suits a portrait screen.
- Sixteen black spheres carry the vocabulary labels. They are buoyant, so they drift
  to the outside of the field, and are held in on X and Z so their pills stay in frame.

Collision search uses a spatial hash, so cost grows with the number of balls rather
than with the square of it. It runs at roughly 1.6 ms per frame for the physics.

## Partner logos

Each cell loads `logos/<slug>.png` and falls back to the partner's name as text if
the file is missing, so the layout never breaks. See `logos/README.md` for the
filenames and the image requirements.

The marks are normalised by **optical area** rather than by height — a tall square
symbol scaled to the same height as a long wordmark reads much smaller than it
should. Seoul Metropolitan Government and Hongik IDAS carry an extra manual boost,
because both are symbol-plus-caption lockups whose bounding box overstates how big
they actually look.

## Hosting

The entry file is `index.html`, so GitHub Pages serves it at the repository root.
Enable it under **Settings → Pages → Build and deployment → Source: Deploy from a
branch → `main` / `(root)`**. The site is fully static — nothing to build.

## Editing the content

Speakers, the run sheet, the Love and Excellence values, and the hero labels are all
plain arrays near the top of the `<script>` block — `SPEAKERS`, `RUNSHEET`, `VALUES`,
`LABELS`. Body copy lives in `data-en` attributes on the markup. Korean translations
are still present in `data-ko` but are not currently shown; the language toggle was
removed.
