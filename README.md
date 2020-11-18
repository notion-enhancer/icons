# icons

a collection of custom icon sets for use within [notion-enhancer's](https://github.com/notion-enhancer/notion-enhancer/) **notion icons** extension.

![notion-icons-demo](https://media.giphy.com/media/zSNMMc7UUxDdPEpsNR/giphy.gif)

## usage

1. install [notion-enhancer](https://github.com/notion-enhancer/notion-enhancer/).
2. open the enhancements ui through the enhancer's tray/menubar icon or with `OPTION/ALT + E`.
3. enable the **notion icons** extension.
4. reload notion with `CMD/CTRL + R` or relaunch notion through the enhancer's tray/menubar icon.
5. the icons tab should now be present when you open the page icon selection ui.

## personal icon sets

users can provide their own `json` file to include their personal icon sets.

the `json` file should have one `icons` object which defines an array of icon set objects with the following properties:

| property               | description                                                                                                                                                            | type              |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- |
| `name`                 | display name of the icon set.                                                                                                                                          | string            |
| `source`               | if `sourceUrl` is defined: defines a list of the icons' filenames. otherwise, defines a list of urls, each pointing to an icon.                                        | array of strings  |
| `extension` (optional) | the icons' extension (not necessary if `source` is an array of urls), e.g. `png`, `svg`.                                                                               | string            |
| `sourceUrl` (optional) | defines a base url for all icons in the set.                                                                                                                           | string            |
| `count` (optional)     | if `sourceUrl` is also defined, the `source` filename will be iterated from `0` to `count` with an underscore `_` in between, i.e. `source_0`, `source_1`, `source_2`. | number            |
| `author` (optional)    | name of the icon set's author.                                                                                                                                         | string            |
| `authorUrl` (optional) | link to the author's site.                                                                                                                                             | string            |

### example

the following `json` defines three icon sets taken from [icons8](https://icons8.com/) and [flaticon](https://www.flaticon.com/).

```json
{
  "icons": [
    {
      "name": "Icons8 Fluent",
      "sourceUrl": "https://img.icons8.com/fluent/280/000000/",
      "source": [
        "source-code",
        "forward",
        "fire-element"
      ],
      "extension": "png"
    },
    {
      "name": "Icons8 Mix",
      "source": [
        "https://img.icons8.com/ios/280/000000/source-code.png",
        "https://img.icons8.com/material/280/000000/forward.png",
        "https://img.icons8.com/color/280/000000/fire-element.png"
      ]
    },
    {
      "name": "Freepik Business",
      "sourceUrl": "https://www.flaticon.com/svg/static/icons/svg/3650/",
      "source": [
        "3650403", "3650408", "3650413", "3650417", "3650424",
        "3650429", "3650433", "3650437", "3650440", "3650444",
        "3650449", "3650451", "3650457", "3650462", "3650467"
      ],
      "extension": "svg",
      "author": "Freepik",
      "authorUrl": "http://www.freepik.com/"
    }
  ]
}
```

![custom-icon-sets](https://i.imgur.com/UdaL6WB.png)

## contributing

the default sets of icons used by the extension are pulled directly from this repository.

**have an icon set you want to share?** great! the following explains how you can upload your own icon set for everyone to use.

### icon image files

the recommended size for page icons is 280 x 280 pixels.

icons need to be named in the format of `FOLDERNAME_#.ext` with:

- `#` representing the `#th` icon.
- `ext` representing the icon file type, e.g. `png`, `svg`.

> e.g. the icons in `FC` are named as `FC_0.png`, `FC_1.png` ... `FC_22.png`.

### sprites.png

generate a sprite sheet for your icon set in a [css sprites generator](https://www.toptal.com/developers/css/sprite-generator).

- set paddings to **0**
- align elements **top-down**

the sprite sheet should be named `sprites.png` and placed inside your icon set's folder.

### `icons.json`

information for icon sets are stored in `icons.json`.

`icons.json` consists of an `icons` object which defines an array of icon set objects with the following properties:

| property    | description                              | type   | example                        |
| ----------- | ---------------------------------------- | ------ | ------------------------------ |
| `name`      | display name of the icon set.            | string | `"For Creators"`               |
| `source`    | the icon set's folder name.              | string | `"FC"`                         |
| `extension` | the icons' extension.                    | string | `"png"`                        |
| `count`     | number of icons in the set.              | number | `23`                           |
| `author`    | name of the icon set's author.           | string | `"Minhee Yoon"`                |
| `authorUrl` | link to the author's site.               | string | `"https://dribbble.com/miniY"` |

### helper scripts

`rename-icons.js` can be used to quickly rename icons into the required format.

run the below with `<folder-name>` being the folder name of the new icon set (e.g. `FC`).

```bash
node rename-icons <folder-name>
```
