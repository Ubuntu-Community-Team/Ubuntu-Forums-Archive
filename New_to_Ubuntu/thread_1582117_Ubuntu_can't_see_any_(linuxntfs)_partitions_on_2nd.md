---
title: "Ubuntu can't see any (linux/ntfs) partitions on 2nd hard drive"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by Remagen on 2010-09-26
Here is an odd issue. 

  So, I had two hardrives (sda and sdb); I replaced sda with a 40 gb SSD and reinstalled windows & linux on that without any issues.  

Installing windows first (for easy grub installation) I could see all my partitions on sdb, as expected.  After I installed linux though, also on sda, I found that nothing (fdisk, gparted, testdisk!!) could find any partitions at all on sdb.

  So, why can windows see these partitions but not linux?

---

### Post by jtarin on 2010-09-26
[While not directly related to your question]("http://ldn.linuxfoundation.org/blog-entry/aligning-filesystems-ssd%E2%80%99s-erase-block-size")...I think its an interesting read on SSD's. Note the date though and there could be changes. [And here.]("http://wiki.archlinux.org/index.php/SSD#Partition_Alignment")

---

### Post by jtarin on 2010-09-26
Could you post your ```
fdisk -l
``` from the SSD disk?

---

### Post by Remagen on 2010-09-26
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45fb7625

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        3953    31641600    7  HPFS/NTFS
/dev/sda3            3953        4866     7336960   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2d6674e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976761528+  42  SFS

```

The SSD, is sda, the 1tb disk is sdb, sdb is the disk I'm having issues with.  

There *should* be 2 ntfs partitions and 2 linux partitions (home & swap).  testdisk, after searching for like 2 hrs finds all partitions but the home partition, which is the one I want.

---

### Post by jtarin on 2010-09-26
Is there a particular reason you have the drive formatted the SFS File system?

---

### Post by srs5694 on 2010-09-26
SFS is the "Secure File System." I know nothing about it beyond that, but from your description of what you did, my suspicion is that your partition table became accidentally corrupted. Chances are your best course of action is to delete the partition on /dev/sdb and use [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) to recover your real partitions. That said, I recommend you hold off a few hours in case somebody else has a better suggestion.

---

### Post by Remagen on 2010-09-26
Yeah, thats what I have done, except for the fact that testdisk can't find one partition + windows can see said partitions on sdb which makes me wonder how I managed to half corrupt this.

---

### Post by Remagen on 2010-09-26
If I can just copy and rewrite the partition table from windows, so linux can at least see the 1 ntfs partition I'll be fine.  I just don't want linux to trash that one partition.  

Also, is it important that the ntfs partition is dynamic (split up across two partitions on the same disk)?

---

### Post by jtarin on 2010-09-26
What doyou have on Disk /dev/sdb: 1000.2 GB? Anything you want to keep? If not why not just reformat with the file system you need?
[I found this little tidbit.]("http://groups.google.com/group/microsoft.public.windowsxp.general/msg/6218d52006ba6dfa?pli=1")
Did you ever encrypt this disk before and with what?

---

### Post by Remagen on 2010-09-26
nope, no encryption

---

### Post by jtarin on 2010-09-26
If you have nothing on the drive that is valuable you might try using Windows disk manager to reassign that disk as NTFS or FAT32, whatever it was before. Linux would not assign that label without user or software intervention. [Have you used any products from here?]("http://www.runtime.org/")

---

### Post by srs5694 on 2010-09-27
> **Remagen said:**
> If I can just copy and rewrite the partition table from windows, so linux can at least see the 1 ntfs partition I'll be fine.  I just don't want linux to trash that one partition.  

Also, is it important that the ntfs partition is dynamic (split up across two partitions on the same disk)?

Windows "dynamic disks" (aka Logical Disk Manager, or LDM) are the equivalent of Linux Logical Volume Manager (LVM) configurations. Linux can read these, if the right kernel modules are installed, but once a disk is in LDM form, I don't know of a way to convert it back. In theory, if you knew that the dynamic disks were made up of contiguous blocks, and if you knew the start and end points of each, you could convert back with fdisk; but I wouldn't risk it except with data of so little value that it'd be easier to just throw it away.

Overall, I'd say your best bet is to back up the disk and then do a fresh re-partitioning of it. For cross-platform use, it's best to avoid Windows LDM or Linux LVM. They're useful tools (most of my Linux installations use LVM), but they aren't the best for cross-platform use. Even though Linux can read LDM, AFAIK there are no tools that enable Linux to manipulate the LDM configuration, which can be limiting. I have no idea if there are drivers to enable Windows to read Linux LVM setups.

---

