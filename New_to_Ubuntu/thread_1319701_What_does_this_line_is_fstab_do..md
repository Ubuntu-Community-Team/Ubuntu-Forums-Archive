---
title: "What does this line is fstab do."
date: 2009-11-08
forum: New to Ubuntu
---

### Post by philinux on 2009-11-08
Just wishing to understand a bit more in depth.


```
proc            /proc           proc    defaults        0       0
```

---

### Post by diesch on 2009-11-08
/proc is a virtual file system (that is it doesn't exist on any disk) that contains files providing interfaces to some kernel functions.

As it is not related to a dive the first field in fstab doesn't matter. The other field are like always (mount point, file system type, mount options, dump flag, fsck pass number).

---

