# The UX Review

A single-page editorial landing page for **The UX Review Blog**, presented as a bold, deliberately unpolished publication about tech, design, and digital culture. The interface is a static HTML/CSS implementation with a responsive mobile layout and locally stored visual assets.

## What is implemented

- Fixed navigation with smooth-scroll links to Home, Latest Articles, Authors, and Community.
- Hero section with the “Brutal Thoughts / Bold Ideas” editorial message, featured image, and visual call-to-action buttons.
- Static latest-article cards for Tech, Design, and Culture content, plus trending items and category counts.
- Author cards for Alex Brutal, Arnold Reeve, and Mike Edge, each with local avatar art and generic social-platform links.
- Community/“Join the Rebellion” section with newsletter, Discord, early-access, and reader-submission copy.
- Footer with category labels, newsletter input, and policy links styled as static UI.
- Responsive rules for screens up to 600px in [`css/media.css`](css/media.css).

> **Implementation note:** this repository currently contains a visual/static demo. Article loading, subscription, “join now,” “watch intro,” and “start reading” controls do not have application handlers or backend integrations. The article metadata, trending counts, testimonials, and author bios are content embedded directly in [`index.html`](index.html).

## Tech stack

- Semantic HTML in [`index.html`](index.html)
- Hand-written CSS in [`css/style.css`](css/style.css) and [`css/media.css`](css/media.css)
- Local JPG, AVIF, SVG, and PNG assets under [`images/`](images/)
- Google Fonts `Exo`, loaded remotely from `fonts.googleapis.com`
- No JavaScript, package manifest, build tool, or application backend is present in this snapshot

## Run locally

There is no package manager or dependency installation step. Use a static file server so relative assets and the remote font load consistently:

```bash
git clone --branch main --depth 1 https://github.com/zeyadhatem00/the-ux-review.git
cd The-UX-Review
python3 -m http.server 8000
```

Open <http://localhost:8000/> in a browser. You can also open `index.html` directly, but a local server is the more representative preview.

To stop the preview, press `Ctrl+C` in the terminal.

## Project structure

```text
.
├── index.html                 # Complete page markup and embedded content
├── css/
│   ├── style.css              # Base layout, colors, typography, and components
│   └── media.css              # Mobile breakpoint rules (max-width: 600px)
├── images/                    # Local hero, article, avatar, icon, and favicon assets
└── .github/workflows/
    └── static.yml             # GitHub Pages deployment workflow
```

## Editing the page

1. Update section markup or copy in `index.html`.
2. Adjust desktop styles in `css/style.css`.
3. Check the mobile layout rules in `css/media.css` when changing widths, navigation, cards, or buttons.
4. Keep referenced image filenames in `images/` aligned with the `src` values in the HTML.
5. Refresh the local static server; there is no build or compile step.

The page relies on the externally hosted **Exo** font. If Google Fonts is unavailable, the CSS falls back to the browser's generic sans-serif family. All listed images and stylesheets are local to the repository.

## GitHub Pages

[`static.yml`](.github/workflows/static.yml) runs on pushes to `main` or by manual dispatch. It checks out the repository, configures Pages, uploads the repository root as the Pages artifact, and deploys it with the official GitHub Pages actions. The workflow does not define a custom domain or a repository-specific public URL.

## Scope and limitations

- The “Load More Articles” button is presentational; it does not fetch or append articles.
- Newsletter and community actions are visual controls only: there is no form action, API endpoint, or storage layer.
- Footer category and policy links currently point to `#` placeholders.
- Author social links currently point to the platform home pages (`x.com`, LinkedIn, and Instagram), not individual profiles.
- There are no automated tests or lint/build commands in the repository.
