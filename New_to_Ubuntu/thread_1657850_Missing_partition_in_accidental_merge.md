---
title: "Missing partition in accidental merge"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by AnalysisFailed on 2011-01-01
The boot sector of my computer got corrupted.

I already had separate partitions from an earlier reformatting of my hard drive.

At the time my boot sector got corrupted I was running win7 with Ubuntu 10.10 installed via wubi on a separate partition than my windows OS.

My problem is that once I reformatted my windows partition and installed 10.10 that my "music" partition and the "stuff" partition, the stuff had the wubi install, happened to merge somewhere during the install.

But the stuff partition is nowhere to be found, it takes up data on the disk and gparted is telling me that it's data is somewhere within the music partition.

Testdisk is saying it's in a w2k Dynamic/sfs filesystem whereas parted is saying it's still fat32. Testdisk realizes that it is three separate partitions, I've found the option to backup those partitions, which I assume a reformat would fix the missing bits, but at the moment I do not have access to enough storage space for the backup.

Is there any way to separate them without having to go through a backup?

---

### Post by blazemore on 2011-01-02
Can you post the output of running the command:
```
sudo fdisk -l
```

---

### Post by AnalysisFailed on 2011-01-04
Yes, here it is.

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffe392b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2               1         196     1572864   27  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   *         196        2155    15728640   83  Linux
/dev/sda4            2155       30402   226895032   42  SFS
```

Anyway, during the run of events, some of my tinkering managed to kill the boot sector, and I figured it would be fun to just start over.

---

