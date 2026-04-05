# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A static HTML website hosted on GitHub Pages — Emily's personal homepage and mathematical notes catalog. There is no build step, static site generator, or server-side logic. The two HTML files are served directly by GitHub Pages.

## Repository Structure

- `index.html` — Main homepage with collapsible sections for projects (Darwin Typeface, Clowder Project), papers, and contact info
- `notes.html` — Comprehensive catalog of mathematical notes (~1770 lines), organized by topic with star ratings and page counts
- `css/styles.css` — Shared stylesheet (Alegreya Sans font family throughout)
- `PDFs/` — Mathematical papers/notes (logic, model theory, type theory, categories, etc.)
- `images/` — Logos (Darwin, Clowder) and site assets

## Key Technical Details

- **MathJax**: `index.html` uses MathJax 3 (CDN, tex-svg); `notes.html` uses MathJax 2 (older CDN). Both support `$...$` and `\(...\)` inline math.
- **Fonts**: Alegreya Sans via Google Fonts; Source Code Pro also loaded in `notes.html`
- **FontAwesome**: Loaded in `notes.html` for star rating icons
- **No framework**: Vanilla HTML/CSS/JS throughout. Interactive elements use plain DOM event listeners.
- **Layout**: Content centered at 800px (`div.main`) or 80% width. No responsive breakpoints.

## CI/CD

GitHub Actions (`.github/workflows/ci.yaml`) runs on push/PR but references `script/bootstrap` and `script/cibuild` — these scripts do not exist in the repo. The CI is effectively a no-op inherited from a GitHub Pages theme template.

## Branch Protection

Configured via `.github/settings.yml` (probot/settings):
- Required status check: `script/cibuild`
- Required code owner reviews for `.github/` changes

## Making Changes

Since this is plain HTML with no build system:
- Edit `index.html` or `notes.html` directly
- Test locally by opening the HTML files in a browser
- PDFs are standalone files in `PDFs/` — replace or add files there
- CSS changes go in `css/styles.css`
