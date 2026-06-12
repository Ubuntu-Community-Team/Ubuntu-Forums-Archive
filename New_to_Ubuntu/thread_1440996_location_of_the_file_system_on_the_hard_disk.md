---
title: "location of the file system on the hard disk"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-03-28
how to find the exact location of the file system on the hard dish?? i mean the on which sda it is located????

---

### Post by Paqman on 2010-03-28
There's a few different ways. You could open Gparted, or Disk Utility, or you could type:
```
sudo fdisk -l
```
into a terminal

---

### Post by llamabr on 2010-03-28
also 

```
df -h
```

will tell you the location, with available disk space.

---

