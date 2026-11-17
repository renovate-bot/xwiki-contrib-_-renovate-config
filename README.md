# XWiki Contrib `renovate-config`

The [inherited config](https://docs.renovatebot.com/config-overview/#inherited-config) Renovate applies to **every repository of the [xwiki-contrib](https://github.com/xwiki-contrib) organization**. The Mend-hosted Renovate apps look for it under this exact repository and file name, which cannot be changed.

[`org-inherited-config.json`](org-inherited-config.json):

* extends the [contrib Renovate preset](https://github.com/xwiki-contrib/.github/blob/master/renovate/default.json5), which holds the actual settings: keep them there, not here;
* disables onboarding (`"onboarding": false` with `"requireConfig": "optional"`): Renovate runs on every repository with that preset, without first opening a "Configure Renovate" pull request, and a repository needs no Renovate file of its own.

A repository can still have its own Renovate file (e.g. `.github/renovate.json5`), which is applied on top of the inherited config:

* add or override settings, e.g. extra `packageRules`;
* `"enabled": false` disables Renovate for that repository;
* `"ignorePresets": ["github>xwiki-contrib/.github//renovate/default.json5"]` stops it from using the contrib preset.
