---
title: "error: dependency is not satisfiable..."
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Shnooky on 2009-01-04
Im trying to install madwifi on an eeepc with atheros and i found a guide that gives me the exact steps as far as i can tell...the web site is...

[http://somethingemporium.com/2007/12/the-real-way-to-install-the-new-madwifi-driver-for-the-eee-pc-build-cd-source](http://somethingemporium.com/2007/12/the-real-way-to-install-the-new-madwifi-driver-for-the-eee-pc-build-cd-source)

It tells me to get 2 packages and I have gotten the first package through terminal and the second package gave me an error with the server so i found it on google as a .deb but when i go to install it it says "Error: Dependency is not satisfiable: linux-image-2.6.22-14-386".  Ive got no idea where to go from there so if anyone knows how to fix this problem or install madwifi effectivly on an eeepc with ar2007 any help would be appreciated.

-Shnooky

---

### Post by Bachstelze on 2009-01-04
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

This is what you need.

---

### Post by stderr on 2009-01-04
It could be the deb was compiled for a different kernel to the one you have. Try running

```
uname -r
```

and compare the output to 2.6.22-14

---

