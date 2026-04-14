# Psi Phi LLC Website

Static site built with Jekyll, hosted on GitHub Pages.

## Structure

```
.
├── _config.yml          # Site-wide settings & shared values (contact info, URLs)
├── _layouts/
│   └── default.html     # Wraps every page with <html>, <head>, nav, footer
├── _includes/
│   ├── head.html        # <meta>, fonts, CSS link
│   ├── logo.html        # Reusable Psi Phi SVG logo
│   ├── nav.html         # Top navigation (used everywhere)
│   ├── footer.html      # Site footer (used everywhere)
│   └── nav-script.html  # Mobile menu JS
├── assets/
│   └── css/
│       └── main.css     # ALL styling — design tokens, components, pages
├── images/              # Photos, etc. (keep your existing folder)
├── index.html           # Home page
├── services.html        # Services page
└── signed.html          # Post-signing landing page
```

## How it works

Each page starts with **front matter** (the `---` block at the top) telling Jekyll which layout to use and what variables to inject:

```yaml
---
layout: default
title: Services
description: ...
---
```

The layout (`_layouts/default.html`) then wraps your page content with the shared nav and footer. Edit the nav once in `_includes/nav.html` and it updates everywhere.

## Editing common things

| Want to change… | Edit this file |
|---|---|
| Brand colors, fonts, spacing | `assets/css/main.css` (top of file — `:root` block) |
| Nav links | `_includes/nav.html` |
| Footer content | `_includes/footer.html` |
| Contact info, booking URL | `_config.yml` (then references like `{{ site.contact.email }}` update site-wide) |
| The logo SVG | `_includes/logo.html` |

## Local preview (optional)

GitHub Pages will build automatically when you push, but if you want to preview locally:

```bash
# One-time setup (Mac)
brew install ruby
gem install bundler jekyll

# In the project folder
bundle init
echo 'gem "github-pages", group: :jekyll_plugins' >> Gemfile
bundle install
bundle exec jekyll serve
```

Then visit `http://localhost:4000`.

## Deploying

GitHub Pages with Jekyll is automatic — just commit and push. Make sure your repo settings have Pages set to "Deploy from branch" → `main` → `/ (root)`.

## Adding a new page

1. Create `newpage.html` in the root
2. Add front matter at the top:
   ```yaml
   ---
   layout: default
   title: New Page
   ---
   ```
3. Write your content below. Nav and footer come for free.
