---
title: "mountall: Event Failed"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by sunavch on 2011-02-28
I am running ubuntu lucid (64-bit) on Dell Inspiron 1525. Although all my disks are mounted when I login to gnome, during boot the following error message is displayed -


fsck from util-linux-ng 2.17.2 
/dev/sda4: clean, 212243/730080 files, 2142219/2918400 blocks 
init: ureadahead-other main process (867) terminated with status 2  
mountall: Event failed 
init: ureadahead-other main process (868) terminated with status 2  
mountall: Event failed 
init: ureadahead-other main process (873) terminated with status 2  
mountall: Event failed 
init: ureadahead-other main process (874) terminated with status 2  
mountall: Event failed 
 * Using startpar-style concurrent boot in runlevel S 
 * Starting AppArmor profiles       [180G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 



fdisk -l gives the following output -
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7650    61448593+   7  HPFS/NTFS
/dev/sda2            7651       36962   235447296    7  HPFS/NTFS
/dev/sda3           38416       38914     3999744   82  Linux swap / Solaris
/dev/sda4           36962       38416    11673600   83  Linux

I have Windows vista (32-bit) on the boot partition and I am using NTFS Configuration Tool (ntfs-config) to enable automatic mounting of the NTFS partitions.

Why does mountall keep failing?

---

