## vite-plugin-list-directory-contents

A small vite plugin to list your directory contents.

![](https://wes.io/YEuDPod4/content.png)

**Why?** In development mode, vite will allow you to have as many inputs as you want, simply run `vite .` and the current folder will be served up. Clicking any `.html` files will be compiled by vite (vited?). So, rather than manually type in the paths to all your inputs, this will list all your files so you can click them with ease. Like the good 'ol `Index Of /` days.

### How to use:

1. `npm i vite vite-plugin-list-directory-contents`
2. create a `vite.config.ts` (or .js) like this:

```ts
import { defineConfig } from "vite";
import { directoryPlugin } from "vite-plugin-list-directory-contents";

export default defineConfig({
  plugins: [directoryPlugin({ baseDir: __dirname })],
});
```

3. The first time it's run, the plugin will create an `index.html` for you in your `baseDir`. You can put anything in this file, and it will be processed by vite, but the important part is the `{%DIRECTORY%}` template tag that will be replaced with the directory listing.

4. go ahead and run `vite` from your cli, or set a `"dev": "vite"` in your `package.json scripts"

### Config

directoryPlugin has two arguments:

1. `baseDir` - where do you want to serve the files up from? \_\_dirname is a good choice, but you can set to a subfolder.
2. `filterList` - an array of files to filter out. Defaults to `['.DS_Store', 'package.json', 'package-lock.json', 'node_modules', '.parcelrc', '.parcel-cache', 'dist', 'packages', '.git', '.eslintrc', '.gitignore', '.npmrc', 'tsconfig.json', 'vite.config.ts', '.env', 'development.env', 'production.env']`

## Builds

This plugin is only meant to run in "serve" mode (development). It will be ignored on build.

## Security

You should note that anytime you create a local server listing directory files on your computer, anyone on your local network could find the port and visit your application. This is great, because you can visit your apps from your phone.

This plugin doesn't allow any access to files that vite doesn't already do, but it does list your files, so don't run it on any folders you don't want opened up to your local network.

Vite does already deny common files like `.env`: https://vitejs.dev/config/server-options.html#server-fs-deny

## Contributing

Edit `plugin.ts`, then run `npm run build` to build a copy. Edits welcome :)

You can run `npm run demo` to test things out with some code in the `/demo` dir.
