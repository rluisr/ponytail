# Frozen snapshot

Independent copy of [DietrichGebert/ponytail#729](https://github.com/DietrichGebert/ponytail/pull/729)
(`pascalandr/ponytail` @ `feat/opencode-v2`).

Not a GitHub fork. Upstream is not a remote. Do not `git pull` from
DietrichGebert or pascalandr, and do not `npm publish`.

## Source pin

PR #729 HEAD (untouched tree): `5739980ca253a0918e8eee64a363690892345812`

This repo adds one local commit on top: remap OpenCode's default
entrypoint to the V2 adapter, drop the upstream npm publish workflow,
and add this file.

## Why the extra commit

OpenCode V2 loads `exports["./server"]`, then `main`. It does **not** honor
the `/v2` subpath in `"plugins": ["@dietrichgebert/ponytail/v2"]`.

This snapshot points `main` / `./server` / `.` at
`.opencode/plugins/ponytail-v2.mjs`. The original V1 adapter stays at
`./plugin`.

## OpenCode config

Pin the snapshot commit SHA (full 40 hex), not `main`:

```jsonc
{
  "plugins": ["github:rluisr/ponytail#<snapshot-commit-sha>"]
}
```
