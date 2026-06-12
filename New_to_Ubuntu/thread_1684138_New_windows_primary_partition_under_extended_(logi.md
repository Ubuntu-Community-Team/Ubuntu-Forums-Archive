---
title: "New windows primary partition under extended (logical) parittion"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by redmorning on 2011-02-08
Hi folks,

i had an issue about the partitions on my hard drive, it may have a very easy solution  but i want to be approved of what i will do. Here is its situation;
```

piratejackus@ganj:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdda4dda4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2   *        1658        1671      102400    7  HPFS/NTFS
/dev/sda3            1671       29217   221267287+   7  HPFS/NTFS
/dev/sda4           41624       60802   154045441    5  Extended
/dev/sda5           41624       60468   151367187+  83  Linux
/dev/sda6           60468       60782     2518016   82  Linux swap / Solaris
/dev/sda7           60782       60802      158720   83  Linux


```

another view of the hard disk is attached (which shows the empty allocation too). 
the thing is; i already have a windows recovery (sda1), windows boot (sda2), windows partition -C- (sda3) and an extended partition (sda4) which has the Ubuntu root partition (sda5), Ubuntu boot partition (sda7) and swap partition (sda6) as you can see. i don't have a problem with the extended partitions of course but the problem is i have 100gb empty space and i'd like to create a new windows partition -D- but i  know that the limit for the primary partitions on a disk is 4.

so my question is, if i expand the extended partition (if i can, because as i remember from last time on gparted, it didn't allow me to do that) and then create a new NTFS partition in this new partition under the extended partition, will i be able to create the windows D partition on it?

Thanks in advance.

---

### Post by Paqman on 2011-02-08
> **piratejackus said:**
> 
so my question is, if i expand the extended partition (if i can, because as i remember from last time on gparted, it didn't allow me to do that) and then create a new NTFS partition in this new partition under the extended partition, will i be able to create the windows D partition on it?


You sure can. What probably stopped you last time was that the extended partition was in use at the time. This happens even if you boot from a LiveCD because it automatically looks for and mounts any swap partitions on the disk, to improve performance. If a swap inside an extended partition is mounted, the whole extended partition is locked.

Boot up into a LiveCD, launch Gparted and right click on your swap partition and "swapoff". This should allow you to make changes to your extended partition.

---

### Post by redmorning on 2011-02-08
Thanks **Paqman**,

it was the reason, i'm gonna keep that in mind. so i expanded the extended partition and formatted the empty space as *ntfs*, know i'm managing windows partitions, everything's fine. Thanks for your fast and clean answer man.

ciao!

---

