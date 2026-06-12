---
title: "Ubuntu Linux, 10.10. Partitioning?"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Rhythm on 2011-01-16
So I'm brand new to Linux, and I recently got a new HDD. I decided I'd add it along with Windows 7. So I installed Windows 7, installed anything I needed like flash, then installed Linux. Now when it came up to the menu where it asked me how I'd want to partition the hard drive, I was confused, but I did it. Now, to make sure I partitioned it properly, I want to know how much space my hard drive has on Linux 10.10. I tried going to Computer and I saw a 2 Hard Disks.

500GB Hard Disk:
200GB File System

500GB Hard Disk:
System Reserved

Now I'm guessing that the first one is the amount I partitioned, but what is the second one? Did I do it right?

Also, if I were to change my mind about how much I partitioned, how would I repartition? I'm completely new to Linux, so any help I can get would be great. :D

---

### Post by TeoBigusGeekus on 2011-01-16
```
sudo fdisk -l
```
that's -L, from terminal and post us the output.
Rearranging/resizing your partitions can be done from a live cd, using gparted (Gnome Partition Editor).

---

### Post by erilidon on 2011-01-16
If you want a GUI option I recommend installing Gnome Partition Editor. It's in the Ubuntu Software Center.

---

