---
title: "How to create a partion with specific sector size?"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-02-19
Hello,

I mean in GPARTED, there is nothing possible to do. 
```
32, 64, 128-sector cluster size
```
Is there a way under LINUX?

---

### Post by cariboo on 2010-02-20
Use fdisk in a terminal.

---

### Post by frenchn00b on 2010-02-21
> **cariboo907 said:**
> Use fdisk in a terminal.
```

Expert command (m for help): s
Number of sectors (1-63, default 62): 
Using default value 62
Warning: setting sector offset for DOS compatiblity


```

you see. not possible to read 64 or 128 :( :( 
with fdisk

---

