## This is a starter package using Storybook with Tailwind, scss, css modules and Next.js framework as frontend.

### The packages/addons are needed to be installed with this starter are:

packages:

- storybook
- tailwindcss

styles related packages:

- postcss
- scss

storybook addons:

- storybook-css-modules
- @storybook/addon-postcss
- storybook-addon-sass-postcss

```javascript
// /.storybook/main.js
module.exports = {
  stories: [
    "../stories/**/*.stories.mdx",
    "../stories/**/*.stories.@(js|jsx|ts|tsx)",
  ],
  addons: [
    "@storybook/addon-links",
    "@storybook/addon-essentials",
    "@storybook/addon-interactions",
    "storybook-css-modules",
    {
      name: "@storybook/addon-postcss",
      options: {
        postcssLoaderOptions: {
          implementation: require("postcss"),
        },
      },
    },
    {
      name: "storybook-addon-sass-postcss",
      options: {
        rule: {
          test: /\.(scss|sass)$/i,
        },
        loadSassAfterPostCSS: true,
      },
    },
  ],

  framework: "@storybook/react",
  core: {
    builder: "@storybook/builder-webpack5",
  },
};
```

```javascript
// /.storybook/preview.js
import "../styles/globals.scss";
export const parameters = {
  actions: { argTypesRegex: "^on[A-Z].*" },
  controls: {
    matchers: {
      color: /(background|color)$/i,
      date: /Date$/,
    },
  },
};
```

```css
/* /style/global.scss */
@tailwind base;
@tailwind components;
@tailwind utilities;

@import "./_button"; /*what ever your component scss files you have using in this project */
```

## Don't forget to change all css to scss, all files extension and import.

# Getting Started

## First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## Second, run the storybook server:

```bash
npm run storybook
# or
yarn storybook
```

Open [http://localhost:6006](http://localhost:6006) with your browser to see the result.
