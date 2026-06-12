---
title: "error, please report ???"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by moose12 on 2009-01-27
i got this error message while trying to do an update

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


i have no clue what to do as far as reporting errors. but i did get the dpkg thing figured out.

---

### Post by zvacet on 2009-01-27
**Applications>accessories>terminal** and type

```
sudo dpkg --configure -a
```

---

