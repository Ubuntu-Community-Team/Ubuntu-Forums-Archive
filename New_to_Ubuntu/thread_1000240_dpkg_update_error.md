---
title: "dpkg update error"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by manuleka on 2008-12-02
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i&#7743; getting the above error when trying to install updates... 

how do i tackle this? cheers

---

### Post by sisco311 on 2008-12-02
open a terminal (Applications->Accessories->Terminal)
and type:
```
sudo dpkg --configure -a
```

---

