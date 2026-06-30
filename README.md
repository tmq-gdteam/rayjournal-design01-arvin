# The Ray Bolouri Journal — Static Deployment

Pre-built static deployment artifact for **raybolouriJournal.com** (Domain 1, Theme 1 — The Signal & Noise).

This folder contains the compiled output of the React/Tailwind v4 source project. It is built for hosting at the GitHub Pages project subdirectory:

```
https://tmq-gdteam.github.io/rayjournal-design01-arvin/
```

## How it deploys

`.github/workflows/deploy.yml` publishes the contents of this folder to GitHub Pages on every push to `main`. No build step runs in CI — the static assets here are uploaded as-is.

## Notes

- The app is a client-side SPA (React Router). It was built with Vite `base=/rayjournal-design01-arvin/`, and the router `basename` is derived from that base, so all routes and asset paths resolve under the subdirectory.
- `404.html` is a copy of `index.html` so deep links (e.g. `/essays`, `/about`) load the app instead of a hard 404.
- `.nojekyll` is required so GitHub Pages serves the `assets/` directory without Jekyll processing.

## Re-deploying after source changes

From the source project root:

```bash
VITE_BASE='/rayjournal-design01-arvin/' npm run build
```

Then copy `dist/*` into this folder, refresh `404.html` from `index.html`, and push.
