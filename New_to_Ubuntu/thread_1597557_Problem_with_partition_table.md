---
title: "Problem with partition table?"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by kris148958 on 2010-10-15
Hi ,
   My fdisk -l output of by HD is 

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb190b190

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3648    29302528+   f  W95 Ext'd (LBA)
/dev/sda2   *        1810        2408     4811436    7  HPFS/NTFS
/dev/sda5               1         956     7679007    7  HPFS/NTFS
/dev/sda6            2409        3526     8980303+  83  Linux
/dev/sda7            3527        3648      979933+  82  Linux swap / Solaris

Why /dev/sda1 is showing all the existing blocks(All hdd is shown as a single partition here).
 "print" output in parted gives "Error: Can't have overlapping partitions." I am using 8.04 ubuntu, but the same is the case even with 10.10(checked with live usb) . 10.10 installer doesn't recognise existing partitions(installer shows all 30GB as unallocated in /dev/sda1). Is there a way to install 10.10 without reformating. Please help me...

Thanks in advance,
Kris.

---

### Post by oldfred on 2010-10-15
The extended partition is a container for all logical partitions, but cannot overlap with another primary. You show sda2 inside sda1, the extended.

I would try testdisk and see if it will straighten out your partitions. It looks like sda5 should be sda1 as you cannot have two extended partitions and cannot have a primary in the middle ot the extended.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by srs5694 on 2010-10-15
I concur with oldfred's diagnosis. Personally, I'd try fixing it with fdisk: Type "sudo fdisk -u /dev/sda" (note the "-u"; that's critical!), record the start and end sector values and type (Id) codes for all the partitions (get a printout if possible), delete all the partitions except /dev/sda2, and then re-create them, setting their sizes *exactly* right. I'd triple-check those sizes before using "w" to write the partition table.

That said, I'm very familiar with partitioning, so I trust my own ability and judgment more than I trust a utility to search for partitions. (TestDisk works by scanning for filesystem identifying data, so it can be deceived if there's stray old data in an unfortunate location.) Somebody less familiar with partitions and fdisk would be perfectly justified in preferring to use TestDisk. Use your best judgment on that score. Getting it right with fdisk isn't what I'd call hard, but it does require attention to detail and a moderate understanding of both fdisk and MBR partitions in general. TestDisk isn't completely idiot-proof, but it does require less in the way of attention to detail and understanding.

---

### Post by oldfred on 2010-10-15
If you want the manual way, you also can use sfdisk. I never have used it but here are links to users that have. The slight advantage is you export a text file,update it, & reimport it, so you can review your data.

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
caljohnsmith and meierfra use sfdisk links:
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

Use sfdisk to edit partitions
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

---

### Post by srs5694 on 2010-10-15
Yes, sfdisk is another option. My [Web page on a similar but different problem](http://www.rodsbooks.com/missing-parts/) provides some of the basic instructions for this approach. One problem with this method is that you'd need to recompute the proper size of the extended partition, since sfdisk works in partition start points and lengths rather than start and end points. Doing it in fdisk, you won't need to deal with that; just create the biggest extended partition possible *after* re-creating the former /dev/sda5 as /dev/sda1 (and leaving /dev/sda2 in place).

---

### Post by Pyroman1010 on 2010-10-24
Sorry wrong thread

---

