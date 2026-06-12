---
title: "sda"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by dooob on 2009-06-24
what is /dev/sda* ? 

* = some number

---

### Post by bumanie on 2009-06-24
The first hard drive (master) in your computer. Second hard drive would be sdbx, etc.

---

### Post by H2SO_four on 2009-06-24
partition #

---

### Post by konqueror7 on 2009-06-24
type,
```
blkid
```
you will know what partition is to what sda*, or
```
sudo fdisk -l
```
for a complete list

---

### Post by SunnyRabbiera on 2009-06-24
SDA usually means the main hard disk
SDB, C and etc are all secondary drives.
Some linuxes use hda and hdb etc though but its the same basic deal.

---

### Post by meindian523 on 2009-06-24
sda is the first hard drives,sda* is the*th partition on the the first hard drive.Second hard drive would be sdb,third sdc,and so on.If *<=4,it's a primary partition,if >4,a logical partition.

---

