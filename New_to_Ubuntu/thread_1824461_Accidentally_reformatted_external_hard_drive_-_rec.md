---
title: "Accidentally reformatted external hard drive - recover files?"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by lxndrlng on 2011-08-13
Hello  - searching for a little expert direction,please. I've very recently begun the switch to Ubuntu 10.10 and have reformatted my 250gb filesystem partition (External usb) from NTFS to Ext3 so I can write to the drive. Anyway, in doing this I've subsequently deleted everything that was quite important to me on it and am rather desperately searching for a way to recover these files as soon as possible. I've done a little research and there seem to be methods of doing so via payed-for-programs that can do such things.. except, they are made for Windows, and I've performed the reformatting through the Gparted UI tool in Ubuntu. I will pay for these programs if they will work (I have set up the computer to dual boot with Vista) on Ubuntu, but would like to find a different method if at all possible..

A very careless mistake; just looking for any remedy. I don't really know what to do.

Thank you so much in advance for any information.

---

### Post by elgordodude on 2011-08-13
Ouch! That sounds like a rough day.

In theory yes, but it probably won't be easy, or quick, and you may not get all of your data back. I would start here, this lays the process out nicely. Please read the whole post before doing anything, the fewer things you try to do to the drive the better off you'll be.

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Good luck, hope it goes well for you.

---

### Post by GMachine_24 on 2011-08-14
[Note: You might want to read the last link in this post as TestDisk - if it works - seems to be what you need.]


I use Clonezilla to back up or copy a hard drive or partition and I think - using the right ancillary tools - you are supposed to be able to pull data off a disk using a special RescueCD. I am NOT that familiar with rescuing a hard drive with the RescueCD - so proceed with caution.

This might work because Clonezilla and dd do, I believe, a sector-by-sector copy of a hard drive. Please be sure to read limitations.

Here is a link:

```


http://clonezilla-sysresccd.hellug.gr/recover.html


```


An ehow page which mentions Clonezilla and another free open-source program called TestDesk, which supposedly can recover some data - it is here

```


http://www.ehow.com/list_6982343_open_source-hard_drive-recovery-tools.html


```


TestDisk seems too good to be true - but who knows??

```


Here is the link to the TestDisk site:


http://www.cgsecurity.org/wiki/TestDisk


And here is what the site says about TestDisk:

Testdisklogo clear 100.png 	
TestDisk, Data Recovery

TestDisk is OpenSource software and is licensed under the terms of the GNU General Public License (GPL v2+).

TestDisk is powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting a Partition Table). Partition table recovery using TestDisk is really easy.

TestDisk can

    * Fix partition table, recover deleted partition
    * Recover FAT32 boot sector from its backup
    * Rebuild FAT12/FAT16/FAT32 boot sector
    * Fix FAT tables
    * Rebuild NTFS boot sector
    * Recover NTFS boot sector from its backup
    * Fix MFT using MFT mirror
    * Locate ext2/ext3/ext4 Backup SuperBlock
    * Undelete files from FAT, exFAT, NTFS and ext2 filesystem
    * Copy files from deleted FAT, exFAT, NTFS and ext2/ext3/ext4 partitions. 

TestDisk has features for both novices and experts. For those who know little or nothing about data recovery techniques, TestDisk can be used to collect detailed information about a non-booting drive which can then be sent to a tech for further analysis. Those more familiar with such procedures should find TestDisk a handy tool in performing onsite recovery. 



```

Like I said - seems too good to be true but I am def going to add it to my box of tools and try it.

good luck

gm

---

### Post by varunendra on 2011-08-14
Try TestDisk/PhotoRec first. If it doesn't succeed, and the data is really very important to you, you may wish to invest in Rtools, network addition if affordable. Rtools has a boot CD version that is platform independent.

Besides, make sure not to perform any task (while attempting recovery or anyway otherwise) that has risk of 'writing' on the target partition/disk. You have to perform read-only operations on it until the desired files are recovered.

Considering above, you may also wish to create an 'image' of the partition/disk using test disk (under 'advanced' options) if you are not sure about 'read-only' nature of an operation you are going to perform (testdisk operation is read-only unless you select the source partition as the target for the recovered files).

---

