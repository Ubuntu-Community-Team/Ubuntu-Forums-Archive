---
title: "Update Manager..."
date: 2010-09-29
forum: New to Ubuntu
---

### Post by Rician on 2010-09-29
when i try to install update with update manager i get --> Software index is broken.. What do i do?? 

Also, when i try to open Synaptic Package manager i get --> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i did that sudo dpkg thing in terminal but still get the same error....

Help please?

Thanks

---

### Post by hhh on 2010-09-29
What happens if in a terminal you run ```
sudo apt-get -f install
```?

-edit- if that still fails, try this, ignoring any errors...
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

