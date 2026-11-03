# Soul2 Mobile Extension — update hosting

Repository: https://github.com/nut2rq/Soul2FF-Ex

## Confirmed Mozilla add-on identity

- Add-on name: Soul2 Mobile Extension
- UUID / Gecko ID shown by AMO: `soul2-mobile-extension@example.invalid`
- Update manifest URL: `https://raw.githubusercontent.com/nut2rq/Soul2FF-Ex/main/updates.json`

## Required manifest configuration

Merge this into the existing `browser_specific_settings.gecko` object in the extension's root `manifest.json` (do not replace the rest of the manifest):

```json
{
  "id": "soul2-mobile-extension@example.invalid",
  "update_url": "https://raw.githubusercontent.com/nut2rq/Soul2FF-Ex/main/updates.json"
}
```

The ID must exactly match the UUID shown in Mozilla Developer Hub and the key in `updates.json`.

## Update manifest

The repository root file `updates.json` advertises version 0.3.0 and points to:

`https://github.com/nut2rq/Soul2FF-Ex/releases/download/v0.3.0/Soul2-Mobile-Extension-0.3.0.xpi`

That download URL will not work until a GitHub Release with tag `v0.3.0` exists and the signed XPI is uploaded as the exact asset name `Soul2-Mobile-Extension-0.3.0.xpi`.

## Publishing sequence

1. Upload the complete extension source to the repository root.
2. Merge the ID and update_url above into the existing root `manifest.json`.
3. Submit the XPI to AMO as an unlisted add-on and download the signed XPI.
4. Create GitHub Release tag `v0.3.0`.
5. Attach the signed XPI using the exact asset name above.
6. Open `https://raw.githubusercontent.com/nut2rq/Soul2FF-Ex/main/updates.json` and verify that it returns valid JSON.

Do not publish an unsigned XPI as an update. Keep the UUID and update_url stable for future versions. For later versions, update the version and signed XPI URL in `updates.json`.

Note: This repository setup does not itself prove that Firefox Android automatic updates work. Test update discovery with a signed installation and a later incremented version.
