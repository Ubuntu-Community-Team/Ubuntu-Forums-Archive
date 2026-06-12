---
title: "How to fix update issue"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by jonathan F on 2009-04-07
Hi ...sorry new to this but how do I do the following to fix inability to add update?

Thanks


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by taurus on 2009-04-07
Close down the update manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by geezerone on 2009-04-07
Open a terminal (ctrl T if I remember correctly) and copy/paste ```
dpkg --configure -a
``` and hit enter.

---

### Post by jonathan F on 2009-04-07
Thanks....seems to have done the trick.

J

---

