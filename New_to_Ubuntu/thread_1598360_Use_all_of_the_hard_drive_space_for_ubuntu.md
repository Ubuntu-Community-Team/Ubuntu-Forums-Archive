---
title: "Use all of the hard drive space for ubuntu"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by Uruk-hai on 2010-10-16
So I have installed ubuntu. Everything works fine I mounted my c drive. But the problem is I cant figure out how to use alll of my hard drive space. It says I only have like 5 GB left. I have a 500GB hard drive. How do I solve this? I want to put all of my music on the music player but It says I don't have permission? i don't understand this...
Thanks.

---

### Post by sikander3786 on 2010-10-16
Please run

```
sudo fdisk -l
```

from terminal and post the output so we have a better idea of your partitions.

---

### Post by mathay on 2010-10-16
Hi, Uruk-hai.

Do you have GParted on a live CD?

Here, check out this tutorial. Hopefully it helps: [https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)

---

### Post by alexan on 2010-10-16
Also, there are other OS installed (windows XP, other linux/ubuntu installation)?
If you want to use the whole HD the best deal is a complete wipe off directly from the installer of ubuntu (no other OS, just your Ubuntu)

---

### Post by Uruk-hai on 2010-10-16
> **sikander3786 said:**
> Please run

```
sudo fdisk -l
```

from terminal and post the output so we have a better idea of your partitions.

here. Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       59527   478110465    7  HPFS/NTFS
/dev/sda3           60742       60802      484352   82  Linux swap / Solaris
/dev/sda4           59528       60742     9751553    5  Extended
/dev/sda5           59528       60684     9285632   83  Linux
/dev/sda6           60684       60742      464896   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by sikander3786 on 2010-10-17
You want to use all the available space on your hard disk for Ubuntu? There is an NTFS partition, you want to keep the data or completeley remove everything? Also, you've got 2 Swap partitions. Any purpose behind that or you got them accidently?

You can delete the un-needed partitions using gparted and then resize to make them look like a single one. You can delete the unwanted partitions from Ubuntu install but for resizing your root partition, you'll need to boot a live CD. See here.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by oldos2er on 2010-10-17
Can you post the output of ```
df -h
``` ?

---

