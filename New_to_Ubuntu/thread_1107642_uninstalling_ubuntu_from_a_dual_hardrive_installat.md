---
title: "uninstalling ubuntu from a dual hardrive installation"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by engellenkatu on 2009-03-27
I have windows xp on my original harddrive C. and Ubuntu 8.10 on another hardrive i. on the same computer. I didn't want to partition the C drive and put both os on the same disc in case I didn't like Ubuntu. 
I want to uninstall unbuntu from the 2nd drive and just use the 2nd drive for backing up my main drive with just windows xp as the os. with the xp os on the C drive of course. 


I'll install ubuntu on another separate computer later on with ubuntu
as the only os on it.
I have unbuntu 8.0 on a cd. But installed the os on the 2nd drive without partitioning. I gave it the entire 2nd drive. 

How do I get ubuntu off this 2nd drive? Totally off? I have ubuntu gnome 8.10

---

### Post by SunnyRabbiera on 2009-03-27
Well if this is on a secondary hard drive you can tell XP to just reformat the Ubuntu partition to say NTFS or something assuming you can see the Ubuntu drive from XP.
If you cant try this:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

It should be able to let XP see your EXT3 drive (thats the filesystem Ubuntu uses)

---

### Post by Yvan300 on 2009-04-09
Just boot up using the live cd, go into gnome partition editor and use that to reformat your drive to fat32,(fat32 because ubuntu and windows can read and write to it) and if you installed grub as the boot loader then after formatting you will have to get your xp cd and run the command fixmbr, that will restore xp's boot loader :)

---

### Post by bowgart on 2009-11-03
> **Yvan300 said:**
> Just boot up using the live cd, go into gnome partition editor and use that to reformat your drive to fat32,(fat32 because ubuntu and windows can read and write to it) and if you installed grub as the boot loader then after formatting you will have to get your xp cd and run the command fixmbr, that will restore xp's boot loader :)


[SIZE=2][FONT=Courier New]I have installed Desktop 9.10 on my HP NC6000 dual boot with XP, although the install went well it crashes prior to the main screen appearing.  I have checked the install cd and it passes. I am not looking to install 9.04[/FONT][/SIZE][FONT=Courier New][SIZE=2], will the installer allow me to remover 9.10 or install over it?  I am a newbe by the way.[/SIZE][/FONT]

---

### Post by agoodliffe on 2009-11-03
I have installed Xubuntu 9.10 on my HP pavilion which looks like this below.
The problem is that I am unable to access my Windows XP from the Grub window. It just hangs with GRUB written in the top left hand corner.
Is it possible to get back into my Windows OS?
I find Xubuntu 9.10 nice and fast and snappy and would like to keep it. Everything else works.

adrian@adrian-laptop:~$ sudo fdisk -l
[sudo] password for adrian: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1d6f1d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            3129       11061    63721822+   c  W95 FAT32 (LBA)
/dev/sda3            1913        3128     9767520   83  Linux
/dev/sda4           11813       12161     2803342+  82  Linux swap / Solaris

Partition table entries are not in disk order
adrian@adrian-laptop:~$ ^C
adrian@adrian-laptop:~

---

