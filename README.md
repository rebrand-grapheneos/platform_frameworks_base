# platform_frameworks_base

> Part of [rebrand-grapheneos](https://github.com/rebrand-grapheneos). See the [main documentation](https://github.com/rebrand-grapheneos/local_manifests) for the complete guide.

Android framework customizations. This is a git2 overlay on top of the upstream [GrapheneOS/platform_frameworks_base](https://github.com/GrapheneOS/platform_frameworks_base) repository (tag `2025110800`).

## What's Changed

Single file modification:

### core/res/assets/images/android-logo-mask.png

The boot animation logo mask. This image defines the logo shape displayed during device boot.

## android-logo-mask.png Specifications

| Property | Value |
|---|---|
| Format | PNG with alpha channel |
| Background | Black (#000000) |
| Foreground | Transparent (alpha = 0) |
| Size | Must match original dimensions exactly |

**How the mask works:** The black areas are opaque (hidden), and the transparent areas define the visible logo shape. The system renders the logo by showing through the transparent cutout.

## How to Create Your Own

1. **Start with your logo** — Any format (SVG, PNG, PSD)

2. **Create the mask image:**
   - Open an image editor (GIMP, Photoshop, Inkscape)
   - Create a new image matching the original file's dimensions
   - Fill the entire canvas with solid black (#000000)
   - Place your logo centered on the canvas
   - Select the logo area and delete it (make fully transparent)
   - The result: black everywhere except where your logo is (transparent)

3. **Export as PNG** with alpha channel preserved

4. **Replace the file:**
   ```bash
   cp your-logo-mask.png frameworks/base/core/res/assets/images/android-logo-mask.png
   ```

5. **Verify by building** — The logo appears during boot animation

## git2 Usage

```bash
# After modifying the logo
cd frameworks/base
.git2/git2.sh push

# Commit
cd .git2
git add -A
git commit -m "update: custom boot logo"
git push
```

## Upstream Reference

- Repository: [GrapheneOS/platform_frameworks_base](https://github.com/GrapheneOS/platform_frameworks_base)
- Tag: `2025110800`
- Commit: `d697c573a824058f1067fc4b317a560d71ce937c`
