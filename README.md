# @ooneex/design

The Ooneex design system — a React 19 component library, icon set, and styling layer built on [Base UI](https://base-ui.com/) and [Tailwind CSS v4](https://tailwindcss.com/).

## Stack

- **React 19** with the `react-jsx` runtime
- **Base UI** for unstyled, accessible component primitives
- **Tailwind CSS v4** + [shadcn](https://ui.shadcn.com/) tokens for styling
- **TypeScript** (bundler resolution, `@/*` → `src/*`)
- **Bun** as the runtime, package manager, and test runner
- **Biome** for linting and formatting

## Layout

```
src/
├── components/   ~50 component families (button, dialog, form, editor, pdf, chart, …)
├── icons/        fill/ and outline/ icon sets, grouped by category
├── hooks/        useControlledState, useAutoHeight, useMobile, useClickOutside
├── utils/        cn (class merging), staleChunk
├── styles/       app.css entry + typography, shape, brand, status layers
└── fonts/        bundled font faces (Space Grotesk)
```

Components follow a consistent pattern: a Base UI primitive wrapped with [`class-variance-authority`](https://cva.style/) variants and the `cn` helper for class merging. See `src/components/button/Button.tsx` for the reference shape.

## Usage

Import components and utilities via the `@/` alias:

```tsx
import { Button } from "@/components/button/Button";
import { cn } from "@/utils/cn";

export const Example = () => (
  <Button variant="outline" size="md">
    Click me
  </Button>
);
```

Pull the styles into your app entry:

```css
@import "@/styles/app.css";
```

## Scripts

```bash
bun install        # install dependencies
bun test           # run the test suite (bun test tests)
bun run lint       # type-check (tsgo) + Biome lint
```

## Conventions

- Strict TypeScript — no unused locals/parameters, no fallthrough cases.
- Commits follow [Conventional Commits](https://www.conventionalcommits.org/) (enforced via commitlint).
- Formatting and lint rules are defined in `biome.jsonc`.
