# samway-ai.github.io

Source for the Samway AI website and product documentation. Samway AI builds retrieval-augmented generation (RAG) chatbots that answer questions from a customer's own content.

This repo holds two things:

- A single-page marketing landing page (`index.html`).
- A set of documentation pages written in MDX, configured by `docs.json`.

## Repository structure

```
.
├── index.html                  # Standalone landing page (inline CSS and one inline script, no build step)
├── docs.json                   # Docs site config: theme, brand colors, navigation
├── index.mdx                   # Docs: Introduction
├── quickstart.mdx              # Docs: Quickstart
├── how-rag-works.mdx           # Docs: How RAG works
├── faq.mdx                     # Docs: FAQ
├── support.mdx                 # Docs: Support
└── chatbot/
    ├── overview.mdx            # Docs: Chatbot overview and key concepts
    ├── knowledge-sources.mdx   # Docs: Adding and maintaining knowledge sources
    ├── customize.mdx           # Docs: Name, instructions, welcome message, appearance
    └── deploy.mdx              # Docs: Going live and improving after launch
```

### Landing page

`index.html` is a self-contained page: it has no framework or bundler, and its styles live in a `<style>` block. The only external resource is the Inter font loaded from Google Fonts. It has sections for features, how it works, get started, and FAQ, and supports light and dark mode through `prefers-color-scheme`.

### Documentation

Each `.mdx` file is one docs page, with `title`, `sidebarTitle`, and `description` in its front matter. Pages use components such as `Steps`, `CardGroup`, `Card`, `Accordion`, `Tip`, and `Note`.

`docs.json` defines the site name, theme (`almond`), brand colors, footer links, and the sidebar. The sidebar has three groups:

| Group | Pages |
| --- | --- |
| Get Started | `index`, `quickstart`, `how-rag-works` |
| AI Chatbot | `chatbot/overview`, `chatbot/knowledge-sources`, `chatbot/customize`, `chatbot/deploy` |
| Resources | `faq`, `support` |

Page names in `docs.json` are file paths without the `.mdx` extension. A new page only shows up in the sidebar once it is added there.

## Working on it locally

There is no `package.json`, build script, or lockfile in this repo, so there is nothing to install or build.

- **Landing page:** open `index.html` in a browser, or serve the folder with any static file server (for example `python3 -m http.server`) and visit `http://localhost:8000`.
- **Docs pages:** edit the `.mdx` files directly. The docs config follows the Mintlify `docs.json` format, so a Mintlify-compatible renderer is needed to preview the pages as a site. None is set up in this repo.

## Deployment

The repo is named `samway-ai.github.io`, which is the naming GitHub uses for an organization's GitHub Pages site. There is no CI or workflow configuration in the repo (no `.github/` directory), so publishing is not defined here. Changes are merged to `main` through pull requests.

## Known gaps

- `docs.json` points to a favicon at `/favicon.svg`, but that file is not in the repo. `index.html` uses an inline data-URI favicon instead.
- `support.mdx` still has the placeholder email `support@example.com`.
