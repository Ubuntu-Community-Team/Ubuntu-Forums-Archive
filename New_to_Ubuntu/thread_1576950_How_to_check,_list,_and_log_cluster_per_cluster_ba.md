---
title: "How to check, list, and log cluster per cluster bad sectors ?"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by honeybear on 2010-09-18
Hello,

I would like to check an old harddisk for bad sectors, and make a clear simple list of them ? Cluster Number and bad blocks.

I havent foudn any tools for that under Ubuntu. An application for that issue would be of great help.. thnks):P

---

### Post by Paddy Landau on 2010-09-19
You could look at the GUI: System > Administration > Disk Utility. It lets you check the file system and view Smart Data (if the hard drive has Smart Data).

I'm not familiar with the command line options. I have used fsck before:
```
fsck -CMf /dev/sdb**x**
```(Replace **x** with the correct letter.)

Also look at e2fsck (assuming you use ext3 or ext4) and badblocks.
```
badblocks -s
```(Read the manual for badblocks before using it.)

---

### Post by honeybear on 2010-09-20
> **Paddy Landau said:**
> You could look at the GUI: System > Administration > Disk Utility. It lets you check the file system and view Smart Data (if the hard drive has Smart Data).

I'm not familiar with the command line options. I have used fsck before:
```
fsck -CMf /dev/sdb**x**
```(Replace **x** with the correct letter.)

Also look at e2fsck (assuming you use ext3 or ext4) and badblocks.
```
badblocks -s
```(Read the manual for badblocks before using it.)

oh thanks !

Actuallmy it is a JFS and I couldnt find a solution to list them ... :(

---

### Post by Paddy Landau on 2010-09-20
> **honeybear said:**
> ... it is a JFS...
I don't know JFS. However, I suggest that you install [jfsutils]("apt:jfsutils") and then see whether badblocks will work.

fsck should work on JFS after you've installed jfsutils.

---

