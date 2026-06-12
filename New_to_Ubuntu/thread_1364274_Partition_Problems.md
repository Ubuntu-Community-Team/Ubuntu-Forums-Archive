---
title: "Partition Problems"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by hellomoto on 2009-12-25
Hi guys, I got a new 1Tb hard disk for Christmas, woop! :P 

I thought I would just partition & format it quickly but something seams a bit odd.

I used gparted to format like this:
20 Gb Ext 4 
20 Gb Ext 4
891.51 Gb Ext 4 

Total: 931.51 Gb

Gparted did the requested operations but then shows the 891.51 Gb partition as having used 14.19 Gb!

I have not put any files onto this partition, can anyone shead any light on this please? - Please see attached thumbnails. 

Cheers & Happy Christmas!

---

### Post by hellomoto on 2009-12-25
I have just read this from here: [https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive") 

> 
Modify Reserved Space (Optional)

When formatting the drive as ext2/ext3, 5% of the drive's total space is reserved for the super-user (root) so that the operating system can still write to the disk even if it is full. However, for disks that only contain data, this is not necessary.

NOTE: You may run this command on a fat32 file system, but it will do nothing; therefore, I highly recommend not running it.

You can adjust the percentage of reserved space with the "tune2fs" command, like this:

 sudo tune2fs -m 1 /dev/sdb1

This example reserves 1% of space - change this number if you wish.

    *

      {i} Using this command does not change any existing data on the drive. You can use it on a drive which already contains data. 

Could this be the reason for it? This partition is going to be used to just back up data on a linux only box, if the ext file system is the reason for this extra use, what type of file system would you use?

---

### Post by hellomoto on 2009-12-25
Ok after running this command: sudo tune2fs -m 0 /dev/sda3

It now only shows as 199mb being used.

I take it if I want to use the ext 4 system I will have to make do with this? Or Should I use NTFS?

---

### Post by b0b138 on 2009-12-25
Yes you are correct. Any file system will use some space. It has to store the journal info somewhere

---

### Post by JC Cheloven on 2009-12-25
> **b0b138 said:**
> Yes you are correct. Any file system will use some space. It has to store the journal info somewhere

Or you could consider using an ext2 filesystem, which hasn't journaling. On the other hand, it has some limitations. For example from [http://www.diskinternals.com/glossary/ext2.html](http://www.diskinternals.com/glossary/ext2.html)

> The ext2 file system has a maximum data size of 4 terabytes, maximum filename length of 255 characters, and has variable length block size. However, other operating system considerations may mean that this full size is often not realizable on any particular operating system. On Linux, for example, restrictions in the block driver mean that ext2 filesystems have a maximum data size of 2047 gigabytes. 

I'd live with the space used by journaling, and using ext3 or ext4 though.

---

### Post by hellomoto on 2009-12-26
Hey thanks guys for confirming previous thoughts. I have decided to keep the ext4 fs. (mainly due having spent 2.5 hours copying 300Gb of data to it!)

Thanks for all your help!

---

### Post by The Real Dave on 2009-12-26
I popped into this thread hoping I could help, and instead you helped me, got me another 20GB of storage, thanks :)

---

