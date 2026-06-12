---
title: "PUBKEY error on updating Lazarus"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by Balf on 2011-04-05
When I try to update Lazarus I get this error:

W: GPG error: [http://www.hu.freepascal.org]("http://www.hu.freepascal.org/")  lazarus-stable Release: The following signatures couldn't be verified  because the public key is not available: NO_PUBKEY 670C48C26A11800F

I am using Ubuntu 10.04 LTS and I get the error after putting 
[http://www.hu.freepascal.org/lazarus/](http://www.hu.freepascal.org/lazarus/) lazarus-stable universe
in the other software section of the software sources and it checks the packages.

---

### Post by kellemes on 2011-04-05
```
gpg --keyserver hkp://pgp.mit.edu:11371 --recv-keys 6A11800F
 gpg --export 6A11800F | sudo apt-key add -
```

from..
[LAZARUS RELEASE VERSION FOR UBUNTU]("http://wiki.lazarus.freepascal.org/Lazarus_release_version_for_Ubuntu")

---

