---
title: "Very low file transfer speeds on the home partition"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by Viva on 2009-05-08
When I try to move large files from another partition to my home partition, the transfer is very slow, only 3 MBps. The transfer speeds are fine if I move the files the other way around. Both the partitions are ext3 and on the same hard drive. Is it possible that one of them is fragmented?

---

### Post by kidders on 2009-05-10
Hi there,

Lots and lots of things could be causing this problem. Fragmentation (or fragmentation of one of the journals) is one possibility.  You can use **fsck.ext3 -n /dev/whatever** to get an idea of the amount of filesystem fragmentation. (The "-n" is _very_ important!) Some other possibilities ...[LIST]
[*]One of your filesystems may be sitting on a RAID array it is poorly optimised for.
[*]One of your filesystems could be extremely large, or contain an unusually high number of files.
[*]Your hard drive might have physical damage.
[*]Your disk geometry may be causing one of your filesystems to underperform.
[/LIST]These are special cases that may not apply to you, but I thought I might as well list as many as I could think of.

---

