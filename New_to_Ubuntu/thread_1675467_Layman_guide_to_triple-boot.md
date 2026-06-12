---
title: "Layman guide to triple-boot"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by victorhugo289 on 2011-01-25
Hi, this is a small triple boot guide for operating systems: Windows98, WindowsXP, and ubuntu10.04 or 10.10.
It's also a guide to put HOME and ROOT into different partitions, at least what you have to do during install.

It was performed on a computer Pentium4 @2GHz, 1GB ram, so it's very basic.

The information is not technical at all, it's the layman guide to triple boot. Take it easy.
--------------------------------------------------------------------------
--------------------------------------------------------------------------
Let's get straight some of the facts about partitioning and basically preparing the hard disk for system.

A hard disk has its geometry printed by factory on it, that's what's called "a low level format". 
Some people call the action of erasing the disk sector by sector a "low level format" but that is inaccurate.
The geometry of hard disks today is very complex to divide it in sectors and stuff like that. But that geometry will often appear in BIOS's but it's called 'legacy' geometry. The system chooses the geometry --sectors, heads, cylinders-- that best suits the size of your drive.
Partitions on a hard drive are not slices on the hard drive, but actually they're just pointers. pointers are information stored at the beginning of the disk that tell where a partition starts and where it ends, they use sector numbers for this.
The pointers that tell where partitions start and end are downrightly laid out at the beginning of the hard disk, all of them, in something that looks like a table. partition table.
On that table the following is recorded:

-----------------------------
MASTER BOOT RECORD
-----------------------------
PRIMARY PARTITION
-----------------------------
EXTENDED PARTITION
----------------------------


What do you have to do to prepare a hard disk for system??

1. the hard disk has to be partitioned.
2. a partition is set to 'active'
3. only primary partitions can be set to active.
4. the first thing you create is a primary partition.
5. then you format that partition to make it suitable for a particular OS.
6. For example if you want Windows 98 you format it with fat16.
7. When you format, you can also put system into it you that it is bootable alone.
8. Be careful when it comes to choosing partition sizes, fat16 format command would not work on a 2GB partition.
9. You have to take care your preparing a partition and formatting it for a specific purpose, for a specific Operating system.
10. Install WIndows 98.
11. Prepare next partition, this time bigger and NTFS.
12. You don't have to create all partitions at once, you can create one by one starting with the primary partition.
13. Install Windows XP, and it will choose the NTFS partition to install itself, alongside Windows 98.
14. Be sure you choose "THis GB partition" on the installer menu of WinXP.
15. Windows 98 and Windows XP will create a dual-boot.
16. Once that is done, proceed to install UBUNTU.
17. For Ubuntu you have to create: HOME partition, and SWAP partition.
18. I recommend --highly-- to use Gparted live CD to prepare partitions with their appropiate formats --Gparted also formats-- EXt4 and SWAP, before inserting the Ubuntu live CD and install because the Ubuntu live CD installer is not very flexible and does things unexpectedly --as you click-- and you can harm your previous Windows partitions.
19. Insert Ubuntu live CD, and choose install.
20. If you're going to separate HOME to a dedicated partition --you have to dedicate SWAP to its own partition mandatorily-- I recommend not doing so now.
21. It is better to install everything on a single partition first.
22. Once Ubuntu is install you can proceed to MOVE Home.
23. Moving Home requires the use of the Ubuntu Live CD. You're gonna work FROM IT to move Home.
24. Moving Home is a process laid out in another file. Not here.
25. Once Ubuntu is installed, the Master Boot Record is occupied by a tiny piece of software called "GNU GRUB".
26. Sometimes GRUB menu will show Windows and somethimes it will not.
27. Don't worry, everything's supposed to be there.
28. What it does is it automatically selects who is the 'active' partition. That's all. No big deal.
29. Partitions in Ubuntu are treated as "/dev/sda" source drive A /device/ and so.
30. There is /dev/sda1,2,3 and 5,6,7,8. Never 4, it is dedicated to extended pointer.

So this is what you have to know in order to deal with all of this.


----------

Note: For Windows98 you start with FAT16, Windows98 has a tool to convert it to FAT32 later on.

I hope it helps someone.

---

### Post by beew on 2011-01-25
Why would anyone still want Win98?! And why would I want to triple boot with two Windows? One may be just necessary evil, but two outdated versions and one is really out??Just saying... :)

But the post is well written and informative on hard disks. I just find the objective a bit strange..

---

