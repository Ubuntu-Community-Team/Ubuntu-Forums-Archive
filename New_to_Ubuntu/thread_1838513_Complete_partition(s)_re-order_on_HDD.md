---
title: "Complete partition(s) re-order on HDD"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by TCAllen07 on 2011-09-03
Having started a new job as a Research Assistant, I need to use a variety of software that's Windows-based. Unfortunately, Wine & VMWare aren't practical solutions (I've tried using large, resource-intensive things like ArcGIS via a VM or Wine and it isn't pretty). 

The problem I've run into is that Windows refuses to be installed in the unallocated space I've provided on my harddrive. A friend says it's likely because Windows will only install itself on the **first** partition on the volume. Anyone know if this is true? 

My main question is whether moving/shifting of all my partitions (/, /home, & swap) is a terrible idea (or even possible), or if I should take x, y, z into consideration. Of course I'll backing everything up just in case, and I have an external HDD w/ more space than my internal...   any thoughts or suggestions (including "dude, you're crazy, don't do it") are *much* appreciated!

---

### Post by Redblade20XX on 2011-09-03
How many primary partitions do you have? Because windows will refuse to install on a partition on a hdd with more than a certain number of primaries. :P

-Red

---

### Post by oldfred on 2011-09-03
Windows is usually the first partition since most system come with Windows. But Windows will install to any primary partition sda1 thru sda4, but first install cannot be to a logical partition. Second installs can be, but all boot files literally are moved to the first install in a primary partition. The primary has to be NTFS with the boot flag or active partition in Windows. Or you have to have unallocated space and a primary available.

Post this to see your current partitions:
```

sudo fdisk -lu
```

---

### Post by TCAllen07 on 2011-09-04
Apologies, I would have replied sooner but I didn't realize there were already replies to my post! I must have my email settings wrong...


Anyway, here's the output from the command, oldfred:

> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1df9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    78125055    39061504   83  Linux
/dev/sda2        78127102   312580095   117226497    5  Extended
/dev/sda5        78127104    82030591     1951744   82  Linux swap / Solaris
/dev/sda6        82032640   263243775    90605568   83  Linux
/dev/sda7       263245824   312580095    24667136    7  HPFS/NTFS

Disk /dev/sdb: 2120 MB, 2120744960 bytes
66 heads, 62 sectors/track, 1012 cylinders, total 4142080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdd: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        8192     7843839     3917824    b  W95 FAT32


That last sda7 partition is the one that the Windows installer created. Evidently, it wasn't on 1-4. Is there any way to change this after the fact, i.e. *without* wiping then re-creating all the partitions in a different order? 

Also, I didn't realize until I looked at it now, that the ntfs partition is *under* sda2...  I've attached a gpart screenshot in case it provides any addtnl help.

---

### Post by oldfred on 2011-09-04
I am not sure if Windows gets confused when extended partitions already exist or not.

If you have nothing in sda7, just delete it. Then shrink the extended partition and create a new primary in the place of where sda7 was. And add boot flag and format to NTFS. You show no boot flag at all.
That works since you have available additional primary partitions.

---

### Post by TCAllen07 on 2011-09-04
That worked perfectly! Made the new partition, successfully installed Windows, and made sure to have an Ubuntu LiveUSB to reinstall GRUB (which also went successfully). 

Thanks very much for your help! I'll mark the thread as solved.

---

### Post by oldfred on 2011-09-04
Glad it worked.:)

---

