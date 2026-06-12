---
title: "Package managers crashed ."
date: 2010-10-24
forum: New to Ubuntu
---

### Post by manish411 on 2010-10-24
1.on running synaptic package manager I am getting the following error--
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

2. on  installing any software package from ubuntu software center I am getting the following error :-The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.
 
How can we solve this problem?

---

### Post by alexandari on 2010-10-24
```
 sudo dpkg --configure -a 
```

in the terminal

```
 sudo apt-get update 
```

---

