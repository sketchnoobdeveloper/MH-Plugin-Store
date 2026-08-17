# MH Admin Plugin

Production plugin repository for the MH Manager host app.

## Layout

```
plugins/mh-admin-plugin/
  latest/MH-Admin-plugin.mhmp   # Latest installable plugin package (auto-updated by CI)
  README.md                     # This file
```

## Auto-update

On every successful MH Admin Plugin build, CI replaces
`latest/MH-Admin-plugin.mhmp` with the freshly packaged plugin and commits the
update to `main`. The file is also mirrored in this repo so the plugin is
always available to install without needing to download a CI artifact.

## Install

1. Build/install the MH Manager app on a device.
2. Open **Plugin Manager**.
3. Tap **Install plugin** and pick `MH-Admin-plugin.mhmp`.
4. The plugin is validated (manifest + signature), installed, and listed under
   **Installed plugins**.

## Security

The `.mhmp` container is signed (MHMP1 scheme, RSA-SHA256). The host only
installs containers that verify against the embedded MH trust anchor. The
plugin also carries the MH plugin APK certificate so only trusted builds can
be launched.