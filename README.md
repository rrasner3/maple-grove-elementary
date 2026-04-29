# Maple Grove Elementary

A small demo website for a fictional elementary school, built with [Astro](https://astro.build) +
[Tailwind CSS](https://tailwindcss.com) and deployed to [Cloudflare Workers Static Assets](https://developers.cloudflare.com/workers/static-assets/).

This project exists primarily to demonstrate content/site updates using
[emdash](https://github.com/anomalyco/emdash).

## Stack

- Astro 5 (static output)
- Tailwind CSS 4 (via `@tailwindcss/vite`)
- TypeScript (strict)
- Cloudflare Workers + Static Assets (`wrangler.jsonc`)

## Project layout

```
src/
├── components/         Header, Footer, NewsCard, StaffCard
├── content/
│   ├── news/           Markdown news posts (one file per announcement)
│   └── staff/          Markdown staff profiles
├── content.config.ts   Content collection schemas
├── layouts/
│   └── BaseLayout.astro
├── pages/
│   ├── index.astro     Home
│   ├── about.astro
│   ├── staff.astro
│   ├── admissions.astro
│   ├── news/
│   │   ├── index.astro
│   │   └── [...slug].astro
│   ├── contact.astro
│   └── 404.astro
└── styles/global.css
```

## Local development

```sh
npm install
npm run dev      # http://localhost:4321
npm run build    # produces ./dist
```

## Deploying to Cloudflare

The site is deployed as Workers Static Assets. The build output (`./dist`) is uploaded
and served by a Worker — no Worker code, just the asset binding configured in
`wrangler.jsonc`.

```sh
# one-time
npx wrangler login

# deploy
npm run deploy
```

After deploy you'll get a `https://maple-grove-elementary.<your-subdomain>.workers.dev` URL.

## Suggested emdash demo edits

Each makes a focused, visible change:

1. **Add a news announcement** — drop a new `.md` file in `src/content/news/`.
2. **Add or update a staff member** — edit a file in `src/content/staff/`.
3. **Tweak the homepage hero** — change the headline or tagline in `src/pages/index.astro`.
4. **Adjust the brand color** — change `--color-maple-600` in `src/styles/global.css`.

Each is a small, isolated change — perfect for a parallel emdash workspace.
