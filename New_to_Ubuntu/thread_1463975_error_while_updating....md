---
title: "error while updating..."
date: 2010-04-27
forum: New to Ubuntu
---

### Post by joenewtzie on 2010-04-27
I keep getting this error while updating...


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6


Any ideas on a fix?

---

### Post by wojox on 2010-04-27
Sure, open your terminal and run these two commands:

```
gpg --keyserver subkeys.pgp.net --recv 632D16BB0C713DA6
```
```
gpg --export --armor 632D16BB0C713DA6 | sudo apt-key add -
```

---

### Post by joenewtzie on 2010-04-27
> **wojox said:**
> Sure, open your terminal and run these two commands:

```
gpg --keyserver subkeys.pgp.net --recv 632D16BB0C713DA6
```
```
gpg --export --armor 632D16BB0C713DA6 | sudo apt-key add -
```

At first I just unchecked everything with PPA under software sources but thanks for that code, got it updated and fixed!

---

