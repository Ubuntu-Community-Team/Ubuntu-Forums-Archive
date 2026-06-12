---
title: "How do I set up a 2nd drive ?"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by ericstrom on 2010-08-05
Currently dual booting Win XP and Lucid Lynx on drive a (/dev/sda). I am pretty much out of space on the drive as it's only 40 GB. I have a second 40 GB drive on my PC and I'd like to use that for day to day file storage (pics, documents....etc). Wondering how I set that up.

When I go to Places/Computer, only the sda drive is showing up. But if I run GParted, I see both drives; /dev/sda and /dev/sdb. Under /dev/sdb, it says 40 GB unallocated. 

GParted seems to give me a couple of options that I'm not completely clear on. If I click ..Device/Create Partition Table, then it says it will it will erase all data on sdb and create a defualt ms dos partition table. I don't have a problem erasing the data on sdb but not sure if an msdos partiton is what I need. On the other hand, I can go to Partition/ New in GParted and create either a new partition table asa primary or extended and I can do it as ext 2, 3, 4 fat32, nfts, linux swap or unformated. 

I have no idea what I'm doing with these options. Just would like to boot up, have this second drive already mounted and be able to store my system files there so I don't have take up space on sda. Right now I have all my files loaded onto DropBox. Would like to have my system files on sdb synch with DropBox.

Any ideas would be greatly appreciated !

---

### Post by furialis on 2010-08-05
Use GParted to format the drive. Make sure it's sdb. If you would like to access that drive from WinXP, you'll need to format it ntfs.

---

### Post by oldfred on 2010-08-05
You want msdos or MBR type partitions (gpt is the other choice for Macs & drives over 2TiB). That gives you 4 primary or 3 primary and one extended where one primary becomes the extended. The extended can hold many additional logical. I generally use 2 or 3 primary partitions and use the extended for the rest of the drive so I can create additional logical partition. With 40GB you may only add two or three partitions anyway.

If you want to share data with windows format a partition to NTFS. If you just want linux data use ext3 or ext4. Not sure about Dropbox compatibility as I do not use it. Someone else may know.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)

---

