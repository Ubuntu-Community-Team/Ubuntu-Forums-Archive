---
title: "Dual boot dilemma"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by nnjond on 2010-07-20
Hi,

I want to add openSuse to my pc so that grub gives me the choise of Ubuntu or oS.
However during instalation, oS by default, places my new partion, Sda3 in /usr. Will that bring about the desired result?

Thanks for your time.

---

### Post by Rubi1200 on 2010-07-20
Posting the output from 

```
sudo fdisk -l
```

would be helpful.

---

### Post by nnjond on 2010-07-21
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea053

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60239   483864576   83  Linux
/dev/sda2           60239       60802     4519937    5  Extended
/dev/sda5           60239       60802     4519936   82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 16013852672 bytes
64 heads, 32 sectors/track, 15272 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006a8f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15272    15638512    c  W95 FAT32 (LBA)
nnjond@nnjond-desktop:~$

---

### Post by Sef on 2010-07-21
> Device Boot Start End Blocks Id System
/dev/sda1 * 1 60239 483864576 83 Linux
/dev/sda2 60239 60802 4519937 5 Extended
/dev/sda5 60239 60802 4519936 82 Linux swap / Solaris

> I want to add openSuse to my pc so that grub gives me the choise of Ubuntu or oS.
However during instalation, oS by default, places my new partion, Sda3 in /usr. Will that bring about the desired result?

No sda3 exists.  How exactly did you try and install openSuse?

---

### Post by techunit on 2010-07-21
Well you are going to face a problem installing openSUSE... that is you already have 3 primary partitions on your harddrive and you must first create a extended partition in your last slot... You can then install openSUSE inside of the extended partition... For a tutorial on creating a extended partition please look at this tutorial on [partitioning in Gparted]("http://ubuntuvideotutorials.wordpress.com/install-ubuntu/guide-to-partitioning/")

---

