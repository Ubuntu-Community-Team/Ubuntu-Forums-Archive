---
title: "Plan to install window 7 but worry will corrupt ubuntu boot loader"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by ubfu on 2009-01-21
I have 3 Os install a hard disk.Install accordingly
1.XP
2.Vista
3.Ubuntu 

I plan to delete the vista partition and try with window 7 beta as the vista isn't my primary OS.

Worry If I install window 7 will mess up current boot loader.Or I don't have an option to choose Ubuntu.:(

Anyone installed it ?

---

### Post by ibutho on 2009-01-21
You can use [Super Grub Disk]("http://www.supergrubdisk.org") to restore grub if its deleted by a Windows installation.

---

### Post by Noblacktie on 2009-01-21
If you're just planning on playing with Windows 7, you could virtualise it in Ubuntu.

Else, it's likely to wipe out the MBR but all you need to do is reinstall GRUB via Super Grub or even just the Ubuntu Live CD/USB.

---

### Post by ubfu on 2009-01-21
I found some guide here but I still don't understand.What is (hdX,Y) ? 
[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)


[hyperdude111]("http://ubuntuforums.org/member.php?u=663352")
> “How to” Dual boot Ubuntu and Windows 7 (Ubuntu installed first)
“How to” Dual boot Ubuntu and Windows 7 (Ubuntu installed first)

I have recently seen many posts from people trying to dual boot Ubuntu and Windows 7 beta, but not succeeding. So I tried it out myself and found a solution.
Index
1.	Obtain a copy of Windows7.
2.	Partition your disk with gparted.
3.	Install Windows7.
4.	Re-install Grub.
5.	Edit Grub to List Windows 7.
6.	Have Fun.
__________________________________________________ ________________________________

1.	Obtain a copy of windows 7. 

Official Microsoft Link - [http://download.microsoft.com/downlo...FRE_EN_DVD.iso](http://download.microsoft.com/downlo...FRE_EN_DVD.iso)

*You can also find a torrent of this but for legal reasons I cannot provide a link. *


2.	Partition your disk 

**This does go wrong in very few circumstances**

Boot from a Ubuntu live cd or a gparted live cd.
Start up gparted, If ubuntu is on the whole disk you need to re-size it by at least 8 gb for Windows 7. (Make sure windows 7 is on the second partition to make it easier for grub) You will be left with some unallocated space on your hard disk if you want you can partition it to NTFS or you can do it later on the windows install.

3.	Install Windows 7

Follow the on screen instructions, Select the un-partitioned space to format and install windows on, or if you already made it NTFS choose your NTFS partition. 

**It will ask for a product key but you have 30 days to do that.**


4.	Re-install GRUB

Now you have windows 7 but it has completely eaten your boot loader so you need to re-install grub. 
Boot from the ubuntu live cd and go to terminal.
Type in terminal:

"sudo grub"
"grub> find /boot/grub/stage1"

That should return your Ubuntu partition in the form of (hdX,Y), use that:

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit

(you don’t need to type the grub> bit)

That has re-installed grub but you can no longer see windows7

5.	Edit grub.
Go to terminal from normal ubuntu and type :

“sudo gedit /boot/grub/menu.lst”

A large text file will open and at the bottom leave a line and add this:

title	 windows 7 beta (Loader)
root	 (hd0,1)
savedefault
makeactive
chainloader	+1

(Do not type this line but if that does not work on re-boot try “hdo,0 or hd0,2” and so on until it works.)

Now that is done you can re-boot into windows 7 and ubuntu happily 

---

