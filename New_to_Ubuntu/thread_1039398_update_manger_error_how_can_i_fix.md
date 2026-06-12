---
title: "update manger error how can i fix"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-01-14
i receive the following error with the update manager how can i fix

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


tks/cheesemaker

---

### Post by taurus on 2009-01-14
Close the update manager window.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by rburkartjo on 2009-01-14
taurus, tks it did the trick/cheesemaker

---

