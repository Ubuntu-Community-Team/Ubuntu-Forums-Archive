---
title: "Number of HD heads"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by SteelCore on 2009-11-23
Using fdisk I got the following result
```
root@stlcore-laptop:~# /sbin/fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007c51e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris
```

AFAIK the maximum number of heads on a modern HD is 16. Can someone plz explain the 255. Thanks in advance.

---

### Post by blazemore on 2009-11-23
The 255 refers not to the physical number of heads (This is implemented in firmware, I don't think the OS even sees it), but refers to the number of heads used for partition tables.

---

