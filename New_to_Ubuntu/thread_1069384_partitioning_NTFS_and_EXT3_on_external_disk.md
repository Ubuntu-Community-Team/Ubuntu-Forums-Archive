---
title: "partitioning NTFS and EXT3 on external disk"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by nathan28 on 2009-02-13
Is partitioning an NTFS partition and an EXT3 partition on a single external disk feasible? (It's an Iomega 1TB Prestige). I have to retain a windows boot on my machine for work and some applications, but prefer (duh) linux. I've backed up the disk (all 30 GB) to a thumbdrive so I ain't skaird, but before I re-formatted (using Gparted?) I thought I'd check in with the forum. Does this work?

---

### Post by cerealtx on 2009-02-13
yah, each partition is seperate

---

### Post by mrbiggbrain on 2009-02-13
> **cerealtx said:**
> yah, each partition is seperate


but remember windows INSISTS on being installed on the first disk drive :-) not the first USB disk, the first disk no matter what.

---

### Post by nathan28 on 2009-02-14
> **mrbiggbrain said:**
> but remember windows INSISTS on being installed on the first disk drive :-) not the first USB disk, the first disk no matter what.

so would it make the most sense to go into windows, make a new partition there, then boot ubuntu and wipe the second partition with mkfs or gparted into ext3? sorry for the noob "how to manage your files across three OS's" questions

---

### Post by blueridgedog on 2009-02-14
Since you are not booting of this, I don't think it matters.  Use Ubuntu (Gparted) to make two partitions (primary) on the device and then format one NTFS and one EXT3.

---

### Post by mrbiggbrain on 2009-02-14
> **nathan28 said:**
> so would it make the most sense to go into windows, make a new partition there, then boot ubuntu and wipe the second partition with mkfs or gparted into ext3? sorry for the noob "how to manage your files across three OS's" questions

disk drives are as follows from a tech point

(0)(0)(0) is your 1st controler, 1st disk (master), 1st partiton.

windows wants to be installed on (0)(0)(X).

say you ahve 2 physical HDD, and a USB drive.

the first disk (0)(0) is partitioned with a FAT32 (0), NTFS (1), and EXT3(3) partion. 

the second disk is partitioned with NTFS(0) and FAT32(1)

if you try and install windows onto (0)(1)(0) first controler, second disk, first partiton... it will not... it will default back to the first possible partiton, and try to install onto (0)(0)(0) [fat32]. however you can install onto (0)(0)(1) first controler, first disk, second partiton.

sorry if its a bit confuseing, but put lightly, windows can only be installed onto the fisrt controlers, first disk, any partiton.

---

### Post by nathan28 on 2009-02-14
> **mrbiggbrain said:**
> disk drives are as follows from a tech point

(0)(0)(0) is your 1st controler, 1st disk (master), 1st partiton.

windows wants to be installed on (0)(0)(X).

say you ahve 2 physical HDD, and a USB drive.

the first disk (0)(0) is partitioned with a FAT32 (0), NTFS (1), and EXT3(3) partion. 

the second disk is partitioned with NTFS(0) and FAT32(1)

if you try and install windows onto (0)(1)(0) first controler, second disk, first partiton... it will not... it will default back to the first possible partiton, and try to install onto (0)(0)(0) [fat32]. however you can install onto (0)(0)(1) first controler, first disk, second partiton.

sorry if its a bit confuseing, but put lightly, windows can only be installed onto the fisrt controlers, first disk, any partiton.

No, got it, that's clear. I'm going to attempt to partition the usb disk after i back up some key pieces this afternoon.

---

