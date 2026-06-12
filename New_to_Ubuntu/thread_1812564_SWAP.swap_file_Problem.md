---
title: "SWAP.swap file Problem"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by u bun tu on 2011-07-26
Hello everyone! I think my SWAP.swap file is taking all of my disk space.

When I run the command in the top directory: ls -l

total 524888
drwxr-xr-x   2 root root      4096 2011-07-15 08:01 bin
drwxr-xr-x   2 root root      4096 2011-07-21 22:21 boot
drwxr-xr-x  15 root root      3900 2011-07-26 08:32 dev
drwxr-xr-x 127 root root     12288 2011-07-26 08:33 etc
drwxr-xr-x   6 root root      4096 2011-07-14 12:38 home
drwxr-xr-x  19 root root      4096 2011-07-14 11:14 lib
drwx------   2 root root     16384 2011-04-25 16:23 lost+found
drwxr-xr-x   2 root root      4096 2011-04-25 15:23 media
drwxr-xr-x   2 root root      4096 2011-04-21 09:52 mnt
drwxrwxr-x   2 root root      4096 2011-07-20 10:54 opt
dr-xr-xr-x 108 root root         0 1969-12-31 16:00 proc
drwx------   9 root root      4096 2011-07-14 12:43 root
drwxr-xr-x   2 root root      4096 2011-07-14 11:14 sbin
drwxr-xr-x   2 root root      4096 2011-03-21 01:39 selinux
drwxr-xr-x   2 root root      4096 2011-04-25 15:23 srv
-rw-r--r--   1 root root 536870912 2011-04-25 16:41 SWAP.swap
drwxr-xr-x  12 root root         0 2011-07-26 08:32 sys
drwxrwxrwt   5 root root      4096 2011-07-26 10:17 tmp
drwxr-xr-x  10 root root      4096 2011-04-25 15:23 usr
drwxr-xr-x  15 root root      4096 2011-04-25 15:53 var

When I run the command: df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mmcblk0p2         3683076   3683076         0 100% /
none                    465724       652    465072   1% /dev
none                    467836         0    467836   0% /dev/shm
none                    467836        80    467756   1% /var/run
none                    467836         0    467836   0% /var/lock

When I run the command: sudo fdisk -l

Disk /dev/mmcblk0: 3965 MB, 3965190144 bytes
255 heads, 63 sectors/track, 482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


It looks like the SWAP.swap file is giant and I don't have any free space anymore.

Is there a way that I can "clean" my system, such as clearing temp files or log files?

Any suggestions would be appreciated! I am an absolute beginner!

---

### Post by oldos2er on 2011-07-26
You're missing some information from the sudo fdisk -l command. Can you post its entire output?

---

### Post by u bun tu on 2011-07-26
> **oldos2er said:**
> You're missing some information from the sudo fdisk -l command. Can you post its entire output?

Sorry about that! Here it is:

Disk /dev/mmcblk0: 3965 MB, 3965190144 bytes
255 heads, 63 sectors/track, 482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1           9       72261    c  W95 FAT32 (LBA)
/dev/mmcblk0p2              10         482     3799372+  83  Linux

---

### Post by oldos2er on 2011-07-26
Normally Ubuntu creates a swap partition on installation, rather than a file. Can you explain how SWAP.swap was created? Also I'm a bit puzzled by the device name /dev/mmcblk0p1, rather than /dev/sda or /dev/hda. Can you describe your system specs, and any other OSes you use?

---

### Post by u bun tu on 2011-07-26
> **oldos2er said:**
> Normally Ubuntu creates a swap partition on installation, rather than a file. Can you explain how SWAP.swap was created? Also I'm a bit puzzled by the device name /dev/mmcblk0p1, rather than /dev/sda or /dev/hda. Can you describe your system specs, and any other OSes you use?
 
I'm not sure how the SWAP.swap file was created. I did recently upgrade my kernel but does it take up that much disk space, more than 2-3 GBs? I haven't really installed any additional software or packages.
 
I'm using a Pandaboard instead of a PC or Netbook. It runs on a 4 GB SD Card.
[http://pandaboard.org/node/300/#specs](http://pandaboard.org/node/300/#specs)
 
The OS that I am using is strictly Ubuntu 11.04.
 
Thanks for your help.

---

### Post by oldos2er on 2011-07-27
536870912 bytes is 512MB, not large at all. Hopefully someone who knows something of Pandaboards will jump in to help.

---

