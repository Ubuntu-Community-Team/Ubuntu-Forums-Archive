---
title: "data transfer from external drive"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by sjreg1 on 2011-06-18
I just built a new server with xubuntu and a bunch of internal hard drives for holding old data and new data.  A lot of the old data is on external hard drives formatted ntfs and the new internal drives are formatted fat32 to interact with windows machines.  I'm having difficulty moving data from the external hard drives to the newly formatted drives on my server.  I can't move data from the externals to the new hard drives except to the hard drive I installed xubuntu on.  Any ideas as to what's causing this or how to rectify it?  I'm looking in to using rsync some how but don't have the experience with it to do anything.  Thanks in advance.

---

### Post by sandyd on 2011-06-18
> **sjreg1 said:**
> I just built a new server with xubuntu and a bunch of internal hard drives for holding old data and new data.  A lot of the old data is on external hard drives formatted ntfs and the new internal drives are formatted fat32 to interact with windows machines.  I'm having difficulty moving data from the external hard drives to the newly formatted drives on my server.  I can't move data from the externals to the new hard drives except to the hard drive I installed xubuntu on.  Any ideas as to what's causing this or how to rectify it?  I'm looking in to using rsync some how but don't have the experience with it to do anything.  Thanks in advance.

Firstly, windows OSes can read NTFS.

Secondly, post the output of 
```

sudo fdisk -l
```

---

### Post by sjreg1 on 2011-06-18
Yes, my windows systems recognize NTFS; I understand that, I didn't say they weren't being recognized.  I just meant I partitioned fat32 instead of ext2.  The output of sudo fdisk -l shows all the drives at capacity.

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d937f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243201  1953512001    b  W95 FAT32

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00040f7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001    b  W95 FAT32

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000490af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       59578   478558208   83  Linux
/dev/sdc2           59578       60802     9826305    5  Extended
/dev/sdc5           59578       60802     9826304   82  Linux swap / Solaris

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f2ca7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001    b  W95 FAT32

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bf130

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243201  1953512001    b  W95 FAT32

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000df356

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      243201  1953512001    b  W95 FAT32

Disk /dev/sdg: 2000.4 GB, 2000397795328 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2468f5bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      243201  1953512001    7  HPFS/NTFS

---

### Post by Hoopz on 2011-06-18
How big of files are you moving??  Fat32 has a max file size limit of 4gb  [http://en.wikipedia.org/wiki/File_Allocation_Table](http://en.wikipedia.org/wiki/File_Allocation_Table)

---

### Post by jmore9 on 2011-06-18
Why didn't you use NTFS for all the drives that will talk to windows machines ?  Linux and Ubuntu have pretty good support for NTFS these days.

I use NTFS for storage on my linux machines so that the single windows (winxp) machine can access the data.  I have not had any problems with the file system or files on them.

I still use winxp because there are no linux drivers for the ati tv wonder 650 pci tv tuner card that is in it.

---

### Post by sjreg1 on 2011-06-18
THat should have been the logical decision in the first place.  I'll give it a shot.  But right now I can't even make a new folder in any of the drives.  The system recognizes all the drives and they're partitioned properly but they just don't seem to respond like they should be.  Most of the files I have are relatively small video and audio files (<100mb).  They only reason some of the drives are formatted ntfs is for a handful of hd videos.

---

### Post by sjreg1 on 2011-06-18
Nevermind.  I think I've got it figured out.  I partitioned to ntfs and it all seems to be moving properly.  Thanks for the tip.

---

### Post by sjreg1 on 2011-06-20
Ok the data is moving fine but now I can't access the machine from my windows laptop.  I followed this tutorial ([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)) and keep getting the same 'windows cannot access this location' error.  I'm on basically a university network (cable plugged into wall, goes to a router, and both the server and my laptop are plugged into the router) and I went through that tutorial thoroughly and still can't get it to work.  Any ideas?  Thanks in advance.

---

