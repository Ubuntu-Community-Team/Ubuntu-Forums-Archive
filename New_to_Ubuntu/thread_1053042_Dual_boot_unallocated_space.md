---
title: "Dual boot unallocated space"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Sunshine1987 on 2009-01-28
I used to dual boot Ubuntu 8.10 and Windows XP, but decided to delete my Windows partition.  Now I have about 15 GB of "unallocated space" that I want to add to my current Ubuntu partition.  How can I do this?  Gparted isn't allowing me to do this, at least with what I tried.  Any help would be appreciated!

---

### Post by avtolle on 2009-01-28
You will need to do this from a Live CD, if you were trying to do it running Gparted from the Ubuntu installation. Once into the partitioner from the Live CD, you will need to move and resize the Ubuntu partition. Before beginning anything involving partitioning, you should back up your data files. 

To allow others to assist, please do ```
sudo fdisk -lu
```from the terminal and post the output here for review.

---

### Post by renzokuken on 2009-01-28
gparetd wont let you probably because you are trying to do it from an actual install while the drive is mounted.

have you tried doing it with gparted from a livecd instead?

---

### Post by ptn107 on 2009-01-28
gparted should work.  The catch is that you can't do it while Ubuntu is running, because gparted requires the drive be unmounted.  The solution is to run gparted from the Live CD (it's already included under System -> Administration).

---

### Post by Sunshine1987 on 2009-01-28
I apologize for not clarifying - I have been using gparted after booting from the LiveCD.  Perhaps since I'm new though, I'm not using it properly.

The following is my sudo fdisk -lu:

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders, total 192426570 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000716a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    27278369    13639153+   7  HPFS/NTFS
/dev/sda2        27278370   192426569    82574100    5  Extended
/dev/sda5       186418323   192426569     3004123+  82  Linux swap / Solaris
/dev/sda6        27278496   186418259    79569882   83  Linux

Partition table entries are not in disk order

---

### Post by Sunshine1987 on 2009-01-28
Bump?

---

### Post by avtolle on 2009-01-28
What I see from the above is that you have your Ubuntu install on a logical partition within an extended partition, while the (former) XP install was on a primary partition. I'm no partitioning expert, but I'm aware that disk space on a primary partition cannot be added into an extended partition. So, perhaps the primary partition (/dev/sda1) should be deleted to create unallocated space; then, the extended partition be selected for "move and grow" to move it into the free area and enlarge it to encompass the additional space. Be aware that on /dev/sda5, which is your swap, you will need to select it and turn swap off ("swapoff" under Partition in the bar) before you will be able to do anything with the extended partition.

---

