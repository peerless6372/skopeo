% skopeo-standalone-verify(1)

## NAME
skopeo\-standalone\-verify - Verify an image signature.

## SYNOPSIS
**skopeo standalone-verify** _manifest_ _docker-reference_ _key-fingerprints_ _signature_

## DESCRIPTION

Verify a signature using local files; the digest will be printed on success. This is primarily a debugging tool, useful for special cases,
and usually should not be a part of your normal operational workflow. Additionally, consider configuring a signature verification policy file,
as per containers-policy.json(5).

  _manifest_ Path to a file containing the image manifest

  _docker-reference_ A docker reference expected to identify the image in the signature

  _key-fingerprints_ Identities of trusted signing keys (comma separated), or "any" to trust any known key when using a public key file

  _signature_ Path to signature file

**Note:** If you do use this, make sure that the image can not be changed at the source location between the times of its verification and use.

## OPTIONS

See also [skopeo(1)](skopeo.1.md) for options placed before the subcommand name.

**--help**, **-h**

Print usage statement

**--public-key-file** _public key file_

File containing the public keys to use when verifying signatures. If this is not specified, keys from the GPG homedir are used.

## EXAMPLES

```console
$ skopeo standalone-verify busybox-manifest.json registry.example.com/example/busybox 1D8230F6CDB6A06716E414C1DB72F2188BB46CC8  busybox.signature
Signature verified, digest sha256:20bf21ed457b390829cdbeec8795a7bea1626991fda603e0d01b4e7f60427e55
```

## NOTES

This command is intended for use with local signatures e.g. OpenPGP ( other signature formats may be added in the future ), as per containers-signature(5). Furthermore, this command does **not** interact with the artifacts generated by Docker Content Trust (DCT). For more information, please see [containers-signature(5)](https://github.com/containers/image/blob/main/docs/containers-signature.5.md).

## SEE ALSO
skopeo(1), containers-signature(5), containers-policy.json(5)

## AUTHORS

Antonio Murdaca <runcom@redhat.com>, Miloslav Trmac <mitr@redhat.com>, Jhon Honce <jhonce@redhat.com>