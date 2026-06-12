---
title: "The Little Red Triangle and this error"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by VinnyJ1701 on 2009-11-20
Hey gang,

Ubuntu tells me my update info is out of date. (the red triangle)  When I do, I get the message below, and the red triangle remains.  What is the best way to correct this?

Thanks

Vince 

[INDENT]W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://host/debian/dists/distribution/Release.gpg](http://host/debian/dists/distribution/Release.gpg)  Could not resolve 'host'

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/INDENT]

---

### Post by falconindy on 2009-11-20
You need to get the key for the repo. There's a few ways, but the simplest is probably:
```
gpg --recv-keys 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
```
After that, run 'apt-get update' and upgrade again.

---

