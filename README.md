# Tailwind Fork Changes

This fork includes two simple changes:

1. Export `index.d.ts` and `base.d.ts` files with type information copied from `@types/jsdom`. This allows the library to be used with TypeScript projects without them complaining about a lack of a types file.
2. Set the `xhr-sync-worker.js` file import to `null` in `lib/jsdom/living/xhr/XMLHttpRequest-impl.js`. This is necessary for bundling this code with `esbuild` for use in our AWS Lambda functions. Normally, a custom `esbuild` plugin could take care of this, but since AWS CDK executes `esbuild` via the command line, we cannot use plugins.

See the `jsdom` documentation [here](https://github.com/jsdom/jsdom/blob/main/README.md).
