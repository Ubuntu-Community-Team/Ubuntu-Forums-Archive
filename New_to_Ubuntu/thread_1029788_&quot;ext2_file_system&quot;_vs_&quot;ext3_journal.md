---
title: "&quot;ext2 file system&quot; vs &quot;ext3 journaling file system&quot; on Re-install"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by kramer65 on 2009-01-03
Hello,

I want to reinstall ubuntu while keeping my old home partition. I found [this guide]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion") which explains how to do that. However, when I select "edit the partition" for the partition on which I want to make the "/" I have to select something under "Use as". It gives 8 options;
[LIST]
[*]ext3 journaling file system
[*]ext2 file system
[*]ReiserFS file system
[*]JFS journaling file system
[*]XFS journaling file system
[*]FAT16 file system
[*]FAT32 file system
[*]Swap area
[/LIST]
I don't know if I need to choose the "ext3 journaling" or the "ext2 file system" for the "/" partition.

Also, what kind of file system do I need to select for my existing "/home" partition?

Thanks in advance!

---

### Post by drs305 on 2009-01-03
ext3 is the standard filesystem for / and /home. Here is an explanation of the different filesystems:
[https://help.ubuntu.com/community/LinuxFilesystemsExplained]("https://help.ubuntu.com/community/LinuxFilesystemsExplained")

If you are reinstalling and trying to preserve your previous /home, make sure you do **NOT** format the partition after you designate your /home partition. Leaving it with whatever it currently has will help ensure /home remains unchanged.

---

### Post by kramer65 on 2009-01-03
Great! Thank you so much!

I will proceed with installing then now!

---

### Post by bobpur on 2009-01-03
First of all, DO NOT format your "Home" partition or you will loose everything on it. If you are setting up a home partition for the first time, it can be EXT3, also. I dualboot so I have a whole drive partitioned as NTFS so it can be read from Ubuntu or WinXP.

Ubuntu uses EXT3, by default, if you format from the Ubuntu cd. 

Goodluck.

---

