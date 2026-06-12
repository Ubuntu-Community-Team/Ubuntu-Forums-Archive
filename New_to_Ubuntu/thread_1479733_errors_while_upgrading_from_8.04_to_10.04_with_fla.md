---
title: "errors while upgrading from 8.04 to 10.04 with flashplugin-nonfree"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by realmoonstruck on 2010-05-11
I had an error while upgrading from 8.04 t0 10.04

the error message was:
```
E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.
```

the output in the terminal was:
```
Errors were encountered while processing:
flashplugin-nonfree
E: Sub-process /user/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
```

---

### Post by realmoonstruck on 2010-05-11
how should i reinstall the package? whenever i try to use synaptic or apt-get i get this same error.

---

### Post by realmoonstruck on 2010-05-11
Solved my problem.

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/365392](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/365392)

Ronny Ager-Wick's solution worked for me.

---

