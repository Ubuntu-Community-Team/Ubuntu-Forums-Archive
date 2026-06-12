---
title: "Partition Name?"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by kamitsukai on 2010-07-20
How do I assign a name to a partition in ubuntu? currently it appears that everytime my NTFS partition is mounted it's given a random name like the one below

```
/media/084ECB7623E40DB1
```

is there anyway to make this stay the same?

---

### Post by Paqman on 2010-07-20
You can set a partition label in Gparted. If you haven't got it installed already, it's a handy thing to have on your system.

---

### Post by oldfred on 2010-07-20
Besides gparted you can use Disk Utility or command line to set labels for partitions. 

Easy way to label partitions
System> Admin.> Disk Utility

WARNING: mke2fs will reformat your partition and set a label at the same time. This will delete any data on the target partition.

To set a label without reformatting use e2label or tune2fs
   1. Make a label and FORMAT:
     # mke2fs -L <label> <dev>
   2. Make a label
      e2label <dev> <label>
      tune2fs -L <label> <dev>

---

### Post by kamitsukai on 2010-07-20
Thanks Paqman & Oldfred:popcorn:

---

