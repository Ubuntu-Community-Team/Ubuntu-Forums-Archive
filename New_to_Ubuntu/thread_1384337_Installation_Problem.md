---
title: "Installation Problem"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by laxmipk1 on 2010-01-18
Hi..all
 
I installed ubantu 8.10 successfully but fin when i login using username and password,nothing was happening and my sysytem gets hanged.
 
here is my system info,
 
OS Name Microsoft Windows XP Professional
Version 5.1.2600 Service Pack 2 Build 2600
OS Manufacturer Microsoft Corporation
System Name HOME-82CD0330A7
System Manufacturer INTEL_
System Model D845GVS1
System Type X86-based PC
Processor x86 Family 15 Model 4 Stepping 1 GenuineIntel ~2400 Mhz
BIOS Version/Date Intel Corp. VA84510A.86A.0052.P19.0503162333, 3/16/2005
SMBIOS Version 2.3
Windows Directory C:\WINDOWS
System Directory C:\WINDOWS\system32
Boot Device \Device\HarddiskVolume1
Locale United States
Hardware Abstraction Layer Version = "5.1.2600.2180 (xpsp_sp2_rtm.040803-2158)"
User Name HOME-82CD0330A7\Administrator
Time Zone India Standard Time
Total Physical Memory 512.00 MB
Available Physical Memory 214.57 MB
Total Virtual Memory 2.00 GB
Available Virtual Memory 1.96 GB
Page File Space 1.21 GB
Page File C:\pagefile.sys

Pls some one help me.I m very eager to explore the ubantu world.
Thanks alot

---

### Post by lev-unr on 2010-01-18
Did the live CD work? 

If not perhaps your install disk was corrupted. You may need to reburn and iso and try again. 

Good Luck.

---

### Post by -kg- on 2010-01-18
> **lev-unr said:**
> Did the live CD work? 

If not perhaps your install disk was corrupted. You may need to reburn and iso and try again. 

Good Luck.

If you do re-burn the .iso and try again (oh, and you did check that the downloaded .iso was not corrupt, right?  You checked it against the md5 checksum?  You may need to re-download it, and if so, use a [torrent]("http://torrent.ubuntu.com:6969/") <-clicky) you need to make sure that you delete the partitions that were created from the previous installation.

The installer doesn't know that some partitions aren't needed anymore, and you won't need the partitions from the previous installation.  It will merely make more partitions (if you have enough room on your hard drive) and make the new installation in those.  You will then have XP, the new installation, and the old installation listed in your GRUB menu.  You will also have two of everything; root, swap, and if you opted to make a separate /home or other partitions, those as well.

If you need a little help on how to do these types of operations, click on the link in my signature below.  It will show you how to launch the partition editor on the Live CD, what everything will look like, and how to perform the operations.  Since all you need to do is delete a couple or three partitions that you won't be needing, it's all really simple and not at all dangerous.  Just make sure not to delete your XP partition(s) and you're good to go.

Then, when you are installing and get to the partitioning section, select the "Use Largest Contiguous Free Space" option.  This will install Ubuntu in the space that the previous installation was using.  That, or if you created other partitions (like /home), you already know to select the Manual Partitioning method.  Either way.

---

### Post by Miljet on 2010-01-18
How did you install Ubuntu? Did you install it alongside Windows, or install it within Windows using WUBI?

---

### Post by -kg- on 2010-01-18
Ah!  Good point, Miljet.  That would change everything.

---

