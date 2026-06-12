---
title: "Failing to boot"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by natman on 2010-10-18
Hi,
My laptop is giving problems with booting, im using Kubuntu 10.04. When i power on, after the GRUB menu i get a black screen with an underscore icon flashing in the top left - it stops flashing then just sits there and thats it nothing happens. I restart again the same problem, third restart seems to fix it, but its just getting annoying now. I have also started up in recovery mode and selected the option to fix grub that doesnt always help either. Can anyone help me? I have attached my partitions
```
natman@natman-laptop:~$ sudo fdisk -l
[sudo] password for natman: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4bcb0fb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       19628   156122112    7  HPFS/NTFS
/dev/sda3           19628       38914   154910721    5  Extended
/dev/sda5           33321       38549    41992192    b  W95 FAT32
/dev/sda6           38549       38914     2928640   82  Linux swap / Solaris
/dev/sda7           19628       21087    11717632   83  Linux
/dev/sda8           21087       33320    98264064   83  Linux

Partition table entries are not in disk order

```

---

### Post by diablo75 on 2010-10-18
Just to be sure, does your hard drive activity stop entirely when the cursor goes away and you're left with a totally black screen?

I haven't used Kubuntu for a while but I would think that it started using the Plymouth bootsplash display manager like Ubuntu did at 10.04.  It still has a lot of compatibility problems (because of proprietary video card drivers).  If you want to get a more detailed view of what your system is actually doing at this time, hit the ESC key (after you seen that blinking cursor appear).  This causes the splash screen to be replaced by all the text output you used to see (years and years ago) at startup.  If there's something hanging during this process this is a pretty good way to see what it is.

---

