# seedfaker-php

PHP FFI binding for [seedfaker](https://github.com/opendsr-std/seedfaker) — deterministic synthetic data generator with 200+ fields and 68 locales.

This repository is a **release mirror** for [Packagist](https://packagist.org/packages/opendsr/seedfaker). Source code lives in the [main repository](https://github.com/opendsr-std/seedfaker/tree/main/packages/php). Releases are pushed here automatically by CI on every tagged version, including pre-built native FFI binaries for supported platforms.

## Install

```bash
composer require opendsr/seedfaker
```

## Requirements

- PHP >= 8.1 with the [FFI extension](https://www.php.net/manual/en/book.ffi.php) enabled
- Linux (x86_64, arm64) or macOS (x86_64, arm64)

The native `libseedfaker_ffi` binary is bundled with the package — no separate build step required.

## Usage

```php
use Seedfaker\SeedFaker;

$f = new SeedFaker(seed: "ci", locale: "en");

$f->field("name");                                        // "Zoe Kumar"
$f->field("phone", e164: true);                           // "+14155551234"

$f->record(["name", "email"], ctx: "strict");             // single record
$f->records(["name", "email"], n: 5, ctx: "strict");      // batch
$f->validate(["name", "email:e164"]);                     // check without generating

$f->records(["name", "email"], n: 100, corrupt: "high");  // corrupted data

SeedFaker::fingerprint();                                 // "sf0-..."
SeedFaker::fields();                                      // all field names
```

## Documentation

- [Quick start](https://github.com/opendsr-std/seedfaker/blob/main/docs/quick-start.md)
- [Field reference (200+ fields)](https://github.com/opendsr-std/seedfaker/blob/main/docs/field-reference.md)
- [Library API](https://github.com/opendsr-std/seedfaker/blob/main/docs/library.md)
- [Full documentation](https://github.com/opendsr-std/seedfaker)

## Issues

Please file issues in the [main repository](https://github.com/opendsr-std/seedfaker/issues), not here. This mirror only receives release commits.

## License

MIT — see [LICENSE](LICENSE).

## Disclaimer

This software generates synthetic data that may resemble real-world identifiers, credentials, or personal information. All output is artificial. See [LICENSE](LICENSE) for the full legal disclaimer.
