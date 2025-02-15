# Aporetic fonts

[ _Aporetic_ is the successor to my _Iosevka Comfy_, mainly because "Iosevka" is a reserved name, but also to simplify the overall project: <https://github.com/protesilaos/iosevka-comfy>. ]

Customised build of the [Iosevka typeface](https://github.com/be5invis/Iosevka), with a consistent rounded style and overrides for almost all individual glyphs in both roman (upright) and italic (slanted) variants.

+ Git repository: <https://github.com/protesilaos/aporetic>.
+ Sample pictures: <https://protesilaos.com/emacs/aporetic-fonts-pictures>
+ Backronym: Aporetic's Predecessor Objects' Reserved Eponym Truly Included "Comfy".

## Principles of the design

_Aporetic_ optimises for inter-glyph and inter-style consistency within the overarching constraint of usability at small point sizes. The shapes are generally round and are picked systematically to both impose a predictable rhythm and keep all characters distinct from each other.

Roman and italic styles are made to look more consistent and less exaggerated than the default upstream Iosevka while retaining their unique qualities. Unlike the default Iosevka style, the upright glyphs do not have a mixture of straight/blocky and curved or serified characters (special exceptions notwithstanding). While the italics do not have calligraphic tendencies that greatly contrast with their counterparts. The differences within each style set and between the styles themselves are more nuanced and thus minimalist. The intent is to make everything feel part of the same predictable aesthetic. Distinctions are drawn on the premise of contributing to the demands of the design in light of usability, without ever calling attention to themselves (as opposed to sporadic calligraphic glyphs amid an otherwise austere presentation which seem to say "look how pretty I am!").

To achieve consistency between roman and italic styles I remove elements of roundedness in the latter's glyphs to make them look a bit sturdier. Otherwise they would feel more rounded than their roman counterparts given the added slant. I do not want that added implicit emphasis of extra roundedness because the slant is already sufficient: to emphasise the emphasis is the kind of exaggeration that _Aporetic_ strives to eliminate.

## Installation instructions

_Please help me fill this in with information about available platforms, such as how to install on Windows or with other package managers_.

### Manual Install on GNU/Linux

Unless you have some exotic system, in which case you know what you are doing, you can install fonts for your local user by copying the `.ttf` files or their directories to `~/.local/share/fonts/`. For system-wide installation, place them in `/usr/share/fonts/`.

Depending on your system, you may need to delete the `ttf` or `ttf-unhinted` builds. Though this is not strictly necessary, as the system knows which one to pick.

**Perform a shallow clone** of this repository to speed things up:

```sh
git clone --depth 1 https://github.com/protesilaos/aporetic
```

Then move the font files/directories where they need to be.

### Install with Guix

Get the latest version with this command:

```sh
guix install font-aporetic
```

Or a specific version with something like:

```sh
guix install font-aporetic@1.1.0
```

### Install with Nix

Use the following command:

```sh
nix-shell -p aporetic
```

## Build information

_Aporetic_ is configured in accordance with the documentation of the upstream project. This practically means that (i) [we clone the official repo](https://github.com/be5invis/iosevka), (ii) define our `private-build-plans.toml` at its root, (iii) install the `npm` dependencies, and (iv) build the `.ttf` files with something like the following for each variant (run from the root of the project):

```sh
npm run build -- ttf::aporetic-sans-mono
```

To build all the _Aporetic_ fonts at once, use this:

```sh
for variant in aporetic{-sans,-serif}{,-mono} ; do npm run build -- ttf::$variant ; done
```

The last update to _Aporetic_ was done on 2025-02-12 using upstream commit `7b39833` (post `v32.5.0`).

Each font file is provided as-is in the hope that it may prove useful, but is otherwise intended only for my private use. Concretely, this means that I will only make changes to the fonts if they fix/improve some style, but I will not accommodate other use-cases (e.g. support the Kitty terminal).
