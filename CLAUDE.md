# auth.orcastration.ai

Authentication portal for the Orca platform. Built with Astro.

## Commands

Requires Node 22 (see `.nvmrc`) and pnpm 10.33.0.

```sh
pnpm install       # install dependencies
pnpm dev           # dev server on localhost:4321
pnpm build         # build to dist/
pnpm lint          # astro check + eslint
pnpm lint:fix      # eslint with auto-fix
pnpm test          # run vitest
pnpm verify        # lint + test with coverage (run before pushing)
```

## Structure

- `src/pages/` — file-based routing, each `.astro` file becomes a page
- `src/components/` — reusable Astro components (PascalCase)
- `src/layouts/Base.astro` — shared HTML shell (meta tags, fonts, design tokens)
- `public/` — static assets (favicon, robots.txt)
- `terraform/` — per-site IaC (S3 + CloudFront via shared module, SPA mode enabled)

## Design Tokens

All visual values are `--orca-*` CSS custom properties from the `@orcastration-ai/design` package. Always use tokens.

## Deployment

- Push to `main` deploys to **dev** (`auth.dev.orcastration.ai`)
- Git tag `v*` creates a GitHub Release and deploys to **prod** (`auth.orcastration.ai`)
- Site ID for SSM parameter lookups: `auth-orcastration-ai`
- SPA mode enabled — CloudFront serves `/index.html` for all unknown routes
