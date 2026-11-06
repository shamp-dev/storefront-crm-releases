# Download page

A single static page (`index.html` + `assets/`) that offers the Windows installer for download.
It always links to the newest installer in the GitHub Releases of `CONFIG.repo` (set at the bottom
of `index.html`) and shows its version and size.

## Publish it for free with GitHub (no card needed)

1. Create a **public** repository, e.g. `storefront-crm-releases`. Your source code stays private.
2. Upload the contents of this folder (`index.html`, `assets/`, `.nojekyll`) to it.
3. **Settings → Pages →** Source: *Deploy from a branch*, Branch: `main` / `(root)` → Save.
   The page goes live at `https://<your-user>.github.io/storefront-crm-releases/`.
4. **Releases → Draft a new release:** tag `v1.0.0`, attach the installer named exactly
   `Storefront-CRM-Setup.exe`, then **Publish**.

The download button now points to that file. If your repository or user name is different,
edit `CONFIG.repo` in `index.html`.

## Releasing an update

1. Bump `version` in `desktop/package.json`, then build the installer on Windows: `npm ci`, then `npm run dist:win`.
2. Create a new release (e.g. `v1.0.1`) in the releases repository and attach the new
   `Storefront-CRM-Setup.exe`. The page switches to it automatically.
3. Submit the new installer to Microsoft as a false positive at
   https://www.microsoft.com/en-us/wdsi/filesubmission ("Software developer" → "Incorrectly detected
   as malware/malicious"). This stops Microsoft Defender from blocking it for your customers. Each new
   version is a new file, so submit each one.
