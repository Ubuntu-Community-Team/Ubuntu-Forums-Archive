---
title: "Format hard disk (NTFS) and other questions"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by asciicat on 2010-06-10
Nothing against ubuntu, I love it, but my little brother "wants games (like fusionfall.com)" lame. So I have windows7 disk, and when I got the install step, I couldn't select the partitions because they need to be NTFS or something.

How do I format this for windows 7?


[SIZE=1]
Also, what does this do?[/SIZE]
```
sudo -s
enter password
fdisk -l
(see /dev/sda or /dev/sdb)
fdisk  /dev/sda(or b[if it exists])
type 'c'
type 'd' 
then press 'w'
```

---

### Post by nhasian on 2010-06-10
if you want to dual boot between ubuntu and windows, you need to create separate partitions on your hard disk for each operating system.  Windows7 needs two partitions and Ubuntu needs two as well.  one for / and one for swap.  you can add/delete/modify partitions from booting the Ubuntu LiveCD and going to System-> Administration-> Gparted Partition Editor

---

### Post by asciicat on 2010-06-10
> **nhasian said:**
> if you want to dual boot between ubuntu and windows, you need to create separate partitions on your hard disk for each operating system.  Windows7 needs two partitions and Ubuntu needs two as well.  one for / and one for swap.  you can add/delete/modify partitions from booting the Ubuntu LiveCD and going to System-> Administration-> Gparted Partition Editor
How much space should I allow for a swap?
I have 60GB for regular, and 3GB leftover.
[EDIT] I think I found it: [http://www.sevenforums.com/installation-setup/17694-partitioning-drive-prepare-windows-7-a.html](http://www.sevenforums.com/installation-setup/17694-partitioning-drive-prepare-windows-7-a.html)
[EDIT2] Should I create it as Primary, Logical, or Extended Partition?
[EDIT3] Made 2 as primary and one is 61GB other is 768MB

---

### Post by nhasian on 2010-06-10
you can have up to four primary partitions.  so if windows7 creates two primary partitions, then you can create one more for root, and then an extended partition where you can put your swap and home partitions.

swap partition should be equal to the amount of ram you have in your computer.

---

