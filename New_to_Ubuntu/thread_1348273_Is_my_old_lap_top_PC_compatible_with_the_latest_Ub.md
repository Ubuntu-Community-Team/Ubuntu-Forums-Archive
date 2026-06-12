---
title: "Is my old lap top PC compatible with the latest Ubuntu"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by jzgtrguy on 2009-12-07
Hi! New here. I was wondering if anyone could tell me if my old lap top is compatible with Unbuntu latest release. It is just running so slow. It takes a half an hour to boot up and is just slow period. I have tried all the things I know how to make it run faster but to know avail 
 
It is configured like this;
 
 
 
OS Name Microsoft Windows XP Professional
Version 5.1.2600 Service Pack 3 Build 2600
OS Manufacturer Microsoft Corporation
System Name WORKSTATION
System Manufacturer FUJITSU
System Model FPC03101AK
System Type X86-based PC
Processor x86 Family 15 Model 2 Stepping 7 GenuineIntel ~2392 Mhz
BIOS Version/Date Phoenix/FUJITSU Version 1.03, 5/12/2003
SMBIOS Version 2.3
Windows Directory C:\WINDOWS
System Directory C:\WINDOWS\system32
Boot Device \Device\HarddiskVolume1
Locale United States
Hardware Abstraction Layer Version = "5.1.2600.5512 (xpsp.080413-2111)"
User Name WORKSTATION\Jeff
Time Zone Pacific Standard Time
Total Physical Memory 512.00 MB
Available Physical Memory 73.16 MB
Total Virtual Memory 2.00 GB
Available Virtual Memory 1.96 GB
Page File Space 1.39 GB
Page File C:\pagefile.sys
 
Here is the hard drive
 
 
Drive A:
Description 3 1/2 Inch Floppy Drive
 
Drive C:
Description Local Fixed Disk
Compressed No
File System NTFS
Size 54.43 GB (58,440,581,120 bytes)
Free Space 36.00 GB (38,659,194,880 bytes)
Volume Name 
Volume Serial Number C4DF8E9D
 
Drive D:
Description Local Fixed Disk
Compressed No
File System FAT32
Size 1.46 GB (1,567,911,936 bytes)
Free Space 215.02 MB (225,464,320 bytes)
Volume Name DISE_BACKUP
Volume Serial Number 3EC4D4C9
 
**I was just wondering if my old lap top was compatible and if it would configure correctly with my WIFI etc.** 
 
Drive E:
Description CD-ROM Disc

---

### Post by lotharmat on 2009-12-07
So Basically it's a 2.something GHz processor with 512 MB of RAM and a 50 GB HDD.

I would say it would!

When was the last time you formatted it and re-installed Windows?

The symptoms you are describing point to an OS that has been messed around with quite alot.

Personally, I'd get a copy of the Live CD for Ubuntu, Pop it in and select the 'Try without making any changes to my computer' option.

Bear in mind though that as you are running it from a CD it will be much slower than running it from HDD.

Let us know how you get on!

---

### Post by sliketymo on 2009-12-07
Just check out the "Hardware Requirements" at Ubuntu.com.You did not indicate what video card your using,so it would be hard to advise you.Some video cards don't play nice with certain versions.

---

### Post by jzgtrguy on 2009-12-07
> **sliketymo said:**
> Just check out the "Hardware Requirements" at Ubuntu.com.You did not indicate what video card your using,so it would be hard to advise you.Some video cards don't play nice with certain versions.
 
 
A) How do I get a Live CD? 
 
B)  Is this my video card? 
 
Name RADEON IGP 340M
PNP Device ID PCI\VEN_1002&DEV_4337&SUBSYS_11A410CF&REV_00\4&1930D262&0&2808
Adapter Type ATI RS200M, ATI Technologies Inc. compatible
Adapter Description RADEON IGP 340M
Adapter RAM 32.00 MB (33,554,432 bytes)
Installed Drivers ati2dvag.dll
Driver Version 5.1.2600.0
INF File oem2.inf (ati2mtag_RS200M section)
Color Planes 1
Color Table Entries 4294967296
Resolution 1280 x 1024 x 60 hertz
Bits/Pixel 32
Memory Address 0xE4000000-0xE7FFFFFF
I/O Port 0x00002000-0x00002FFF
Memory Address 0xDC100000-0xDC1FFFFF
IRQ Channel IRQ 11
I/O Port 0x000003B0-0x000003BB
I/O Port 0x000003C0-0x000003DF
Memory Address 0xA0000-0xBFFFF
Driver c:\windows\system32\drivers\ati2mtag.sys (6.14.01.6316, 556.75 KB (570,112 bytes), 3/3/2003 7:00 AM)

---

### Post by Sef on 2009-12-07
> A) How do I get a Live CD? 


go to [http://ubuntu.com]("http://ubuntu.com")

> B) Is this my video card? 


Yes.

---

### Post by Kevbert on 2009-12-07
It should work with [[COLOR="Red"]Ubuntu[/COLOR]]("http://www.ubuntu.com/") OK. Do you know what the make/model of wireless is ?  It may run a little on the slow side (unless you can increase the RAM), so you may like to take a look at [[COLOR="Red"]Xubuntu[/COLOR]]("http://www.xubuntu.org/") instead.

---

### Post by dzon65 on 2009-12-07
I've installed xubuntu on far less performant machines and worked out nice.

---

### Post by mörgæs on 2009-12-07
If you want to skip Windows and use the machine entirely for Ubuntu: Just burn a CD and install - it is as easy and that. Select 'use the entire drive for Ubuntu' or something like that in the process.

It you want a dual boot, you want to reinstall Windows first (since it does not sound healthy), run a defrag in Windows and then install Ubuntu on the remaining space. 

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

A little more RAM would be nice to have, though not strictly necessary.

---

### Post by rasmus91 on 2009-12-07
I know a guy who has a IBM lap top from the mid 90's It runs faster with the newest Ubuntu than it ever did, so i'd recommend trying!

---

### Post by mivo on 2009-12-07
Try to find out what your wireless adapter is. The rest of the machine seems fine, but the biggest problem is usually the wireless adapter. You can download the free version of Everst (Windows), which will tell you what wireless adapter you have: [http://majorgeeks.com/download4181.html](http://majorgeeks.com/download4181.html)  It will tell you just about everything you'll ever want to know about your computer. Might want to print/save the system specs for later use.

---

### Post by mivo on 2009-12-07
> **rasmus91 said:**
> I know a guy who has a IBM lap top from the mid 90's It runs faster with the newest Ubuntu than it ever did, so i'd recommend trying!

You might want to look up the specs of laptops made and sold in 1995, and how much memory they had. :)

But the topic starter's laptop seems fine, provided he can get his wireless to work.

---

### Post by jzgtrguy on 2009-12-08
> **Kevbert said:**
> It should work with [[COLOR=Red]Ubuntu[/COLOR]]("http://www.ubuntu.com/") OK. Do you know what the make/model of wireless is ?  It may run a little on the slow side (unless you can increase the RAM), so you may like to take a look at [[COLOR=Red]Xubuntu[/COLOR]]("http://www.xubuntu.org/") instead.


What is the difference between Ubuntu and Xubuntu?

---

