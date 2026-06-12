---
title: "Update Manager Error message"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by Boat on 2009-09-26
I get this update manager error. Can anyone tell me how to fix this?

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures were invalid: KEYEXPIRED 1253872053 KEYEXPIRED 1253872053 KEYEXPIRED 1253872053
W: Failed to fetch [http://deb.opera.com/opera-beta/dists/stable/Release](http://deb.opera.com/opera-beta/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by zvacet on 2009-09-26
Applications>accessories>terminal 

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys  F9A2F76A9D1A0061
gpg --export --armor  F9A2F76A9D1A0061 | sudo apt-key add -
```

Hit enter after first command and after second of course.

But if you want latest Opera best way is to download it from Opera web site.[Here.]("http://www.opera.com/browser/download/")

---

