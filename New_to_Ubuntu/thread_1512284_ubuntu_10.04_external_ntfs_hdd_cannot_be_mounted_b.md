---
title: "ubuntu 10.04 external ntfs hdd cannot be mounted because of partition problems"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by lolofak on 2010-06-17
Hi,

I am a first time user of ubuntu and i have been having a hard time with using my 750gig external hdd. It always says that the ntfs signature is missing. i checked the through disk utility and it recognizes the hdd with 4 partitions but in reality it is just 1 big partition. i have tried ntfs-config and still not working. 

my fdisk -l goes :

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000513b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9359    75169792   83  Linux
/dev/sda2            9359        9730     2978817    5  Extended
/dev/sda5            9359        9730     2978816   82  Linux swap / Solaris

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?         410      119791   958924038+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdb4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


i have searched for this problem throughout the forums and i cant find the real problem as to why it keeps reading my hdd with partitions

---

### Post by jtarin on 2010-06-18
[See if this helps]("http://ubuntuforums.org/showthread.php?t=721937")

How did you format this and what did you format it with?

Here's my external with three partitons
```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000837da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       40221   323075151    7  HPFS/NTFS
/dev/sdc2           40222       80441   323067150    7  HPFS/NTFS
/dev/sdc3           80442      121601   330617700    7  HPFS/NTFS
```You'll notice the first partition toggled boot?

---

### Post by Mark Phelps on 2010-06-18
Since you mentioned NTFS, if you have access to an MS Windows box, you can download and install EASEUS Partition Master -- their free version of their partitioning app.  That will allow you to see (and fix if necessary) the partitions using a native MS Window app.

---

### Post by lolofak on 2010-06-19
yes, i have tried doing ntfs-config but it didnt really help. i formatted is using windows xp and it has no problem when i use it on windows. The weird thing is ubuntu sees the hard drive with partitions when i really didnt put any.

yes, i will try to do the eusus as soon as i get a hold of a windows running computer. thanks so much for the suggestions.

---

### Post by CharlesA on 2010-06-19
From the fdisk, it looks like Ubuntu "thinks" there are 4 partitions on that drive, but three of them are super small and "unknown" Does it mount the main partitions, /sdb1?

---

### Post by lolofak on 2010-06-19
Only sdb1 and sdb2 are mountable but if i do try to mount them they still give me the ntfs signature missing error. Im assuming that ubuntu reads the free space and the used space as separate partitions.

---

### Post by John Bean on 2010-06-19
> **lolofak said:**
> i formatted is using windows xp and it has no problem when i use it on windows.

It's not compressed is it? Check the properties on a Windows PC.

---

### Post by CharlesA on 2010-06-19
I'm not sure what NTFS signature missing means exactly, but it doesn't sound good.

I'd suggest making a backup ASAP, just in case.

---

### Post by jtarin on 2010-06-19
Can you open it up in GParted and see if those aren't possibly extended partitions. Ifyou have no data on them just resize them and get rid of the space between them.

---

