---
title: "E: dpkg was interrupted"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by kumar2012 on 2009-12-02
hi guys this was the error message shown when i attempted to update by installing new packages can i know the solution for this pl:(
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please repot

---

### Post by Elfy on 2009-12-02
Open a terminal - Applications > Accessories > Terminal

Run the command it gives

```
sudo dpkg --configure -a
```

---

