---
title: "How to make dual booting Windows 7 and Ubuntu 10.10 netbook correctly"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by KristinaK on 2010-10-25
1. How to dual booting Windows 7 and Ubuntu 10.10 netbook? 

2. How to resize existing Windows 7 partition? 

3. How to select and find Windows 7 partition, should it be formatted as either NTFS or FAT32?

4. What file system I should chose for Ubuntu 10.10 netbook edition?

5. How to be sure that Windows 7 partition has a mount point so I can access it?

How to do it safely and correctly?

---

### Post by cariboo on 2010-10-25
> 1. How to dual booting Windows 7 and Ubuntu 10.10 netbook? 

The Ubuntu install process will let you set up a dual boot

> 2. How to resize existing Windows 7 partition? 

Use the disk management tools to resize your windows partition, you can do this without re-installing. When I setup a dual boot system, I usually divide the disk into 2 equal partitions, for instance If my HDD is 160Gb I allocate 80Gb for Windows and 80Gb for the distribution I'm intend to install.

> 3. How to select and find Windows 7 partition, should it be formatted as either NTFS or FAT32?

The Windows disk management tool will show you the Windows partition, it will be the second partition, it is already formatted to ntfs

> 4. What file system I should chose for Ubuntu 10.10 netbook edition?

If you choose automatic partitioning the partitions will be formatted as ext4. If you select the manual partitioning option, you can choose between, ext4, ext3, ext2, reiserfs and btrfs. Any format will work, but I would suggest staying away from btrfs for now, as it needs a seperate /boot partition.

> 5. How to be sure that Windows 7 partition has a mount point so I can access it?

The Ubuntu file manager will automagically mount your WIndows 7 partition, without you having to do anything except click on it.

> How to do it safely and correctly?

Make sure you have a good backup of your important data before you do anything, then read what is on the screen, don't mindlessly click next, like you would in Windows.

If you netbook has a restore partition, it is probably a good idea to make a backup of it too, if you haven't already.

---

### Post by KristinaK on 2010-10-25
Windows 7 is already installed, so will Ubuntu 10.10 netbook installer recognize all the Windiows 7 discs C D E F?

---

### Post by Mark Phelps on 2010-10-25
> 5. How to be sure that Windows 7 partition has a mount point so I can access it? 

Bad idea to mount your Win7 OS partition read/write.  Asking for filesystem corruption problems.  

If you want to share data, better solution is to create a separate data-only NTFS partition and store your shared data there.  That way, if that partition does encounter problems, you will be able to boot into Win7 yo run CHKDSK to correct them.

---

### Post by viant on 2010-10-28
> **cariboo907 said:**
> The Ubuntu install process will let you set up a dual boot


"Install alongside other operating systems" option does not appear in my screen. What should I do?

---

### Post by Mark Phelps on 2010-10-28
> **KristinaK said:**
> Windows 7 is already installed, so will Ubuntu 10.10 netbook installer recognize all the Windiows 7 discs C D E F?

If all of these are primary partitions, then the next line:

> "Install alongside other operating systems" option does not appear in my screen. What should I do? 

Indicates that you already have the maximum number of primary partitions allowed -- 4 -- and you can not create anymore.  Hence, the installer will NOT offer you that option.

---

### Post by ubunterooster on 2010-10-28
> **Mark Phelps said:**
> If all of these are primary partitions, then the next line:

 			 				"Install alongside other operating systems" option does not appear in my screen. What should I do?"

Indicates that you already have the maximum number of primary partitions allowed -- 4 -- and you can not create anymore.  Hence, the installer will NOT offer you that option.
In other words, If those discs ( C, D, E, and F) are all actually one hard drive you will have a problem. If they are different drives it will be fine

---

### Post by Mark Phelps on 2010-10-28
One way we can find out if they are all on one drive:

Boot into Ubuntu LiveCD.  Open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  This will list out the partitions on your drive(s).

Post that info back here so we can see it.

IF you have only one drive and ALL these partitions are primary, you will have a lot of work ahead because you will have to remove one of the partitions to replace it with an extended partition to hold the new Ubuntu partitions.

---

### Post by amjjawad on 2010-10-28
[Dual Booting]("https://help.ubuntu.com/community/WindowsDualBoot")

I suggest to read this before anything. I would do that as a first step :)

---

