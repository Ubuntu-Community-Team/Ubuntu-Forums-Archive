---
title: "help mounting an ntfs volume"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by scared0o0rabbit on 2010-06-03
I've got 2 drives, hard drive 1 has a windows partition, and my ubuntu partitions.  Hard drive 2 had a 240GB partition (ntfs) that I expanded to fill the full 320GB drive yesterday in windows 7.  I only just installed ubuntu today on this computer for the first time, but I assume the issue I'm having is because I expanded the drive.  When I goto places and click on the name of the partition I get the following error message:

Error mounting: mount exited with exit code 12: Failed to read last sector (625133697): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

Is there some way I can fix this so that it will be mountable in ubuntu or am I looking at having to transfer all 300GB off the drive to somewhere else, then repartitioning it so that it's one partition from the very start?

When I go into the disk utility in the system>Administratin menu and look at the disk in question it shows the original 240GB partition that I expanded, and then it also shows 320GB of "unknown" (adding up to 560GB on a 320GB drive).  Any help would be greatly appreciated.

Edit: this is on ubuntu 10.04.

---

### Post by bumanie on 2010-06-03
In terminal > sudo fdisk -lu and post the output back here

---

### Post by scared0o0rabbit on 2010-06-03
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20932092

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   157292414    78646176    7  HPFS/NTFS
/dev/sda2       157292542   448495615   145601537    5  Extended
/dev/sda5       157292544   165292031     3999744   82  Linux swap / Solaris
/dev/sda6       165294080   262948863    48827392   83  Linux
/dev/sda7       262950912   448495615    92772352   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000141f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625140399   312570168+  42  SFS

---

