---
title: "i don't see ubuntu partition from livecd..help"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by Tryer(ForLife) on 2009-11-13
hello

i had a dualboot, win xp and ubuntu jaunty 9.04, on the same hard disk
then i added win7 on that same hard disk and it owerwriten grub, so now i don't see ubuntu, i can't boot in to it...

i don't wanna install grub again, i found a way to use windows boot loader, but i need my old menu.lst from /boot/grub back....but i can't access ubuntu

so i tried booting the live cd so that i can pickup the menu.lst, BUT when i entered the live cd, first it askes me for some username and password, i don't know which password, i tried my own, no success i don't understand, then it entered as user ubuntu, but from there i can't see my ubuntu partition, i can access to some Filesystem partition in Computer, but there i can't see /boot/grub....i don't think that that is my real Filesystem cause i can't see my partition under System Monitor > Fileysystem....

how can i open my real ubuntu instalation and access menu.lst?
thanks

---

### Post by nothingspecial on 2009-11-13
I ought to learn to read

---

### Post by Tryer(ForLife) on 2009-11-13
ok i did read and i managed to find menu.lst
new problem came up
Error 17: File not found....
when i installed windows 7, i resized the partition on which i already had xp and ubuntu...
did i mess something up with paths?

---

### Post by ukripper on 2009-11-13
It is never recommended to install any form of Windows after you have installed ubuntu as it messes with the MBR. anyway back to the solution - 


Method 1 - Restore grub from live cd [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Method 2 - Download the supergrub disk live cd/usb and restore grub from there. [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Tryer(ForLife) on 2009-11-13
ok quick question, will i have options for both win7 and xp when i restore grub?

---

### Post by Tryer(ForLife) on 2009-11-13
ok, like i figured, i fixed the grub, now i only have xp and ubuntu to boot from...
what do i have to do to add win7?

EDIT

Nevermind, it work for both win7 and xp when i pick xp....
that's all i needed, thank you all for your patience..

---

### Post by Eddie Wilson on 2009-11-13
If you have a dual boot already the best way is to backup data in your Ubuntu install, and XP install if needed, install Windows 7 (it should see only the ntfs partition). After that reinstall Ubuntu on the linux partition. The new Grub2 will pickup the Windows 7 install and display it. OR after you install Windows 7 you can just repair or reinstall Grub. Then while in Ubuntu update Grub.

Its not all that hard. I've done it for several people.

---

### Post by Eddie Wilson on 2009-11-13
Oh well. Late again.

---

### Post by ukripper on 2009-11-13
> **Tryer(ForLife) said:**
> ok, like i figured, i fixed the grub, now i only have xp and ubuntu to boot from...
what do i have to do to add win7?

Boot into ubuntu and then in terminal type:
```
sudo gedit /boot/grub/menu.lst
```

and add below entry:
> 
title Windows 7
root (hd0,**x**)
savedefault
makeactive
chainloader +1 

Replace **x** with the partition you installed win 7 on if on same drive. i assume it could be 2. give it a shot.

if that doesn't work just post your menu.lst here and output of fdisk:
```
sudo fdisk -l
```

---

### Post by Tryer(ForLife) on 2009-11-13
ok, here's the situation with the disks

> Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01b701b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2137    17165421    7  HPFS/NTFS
/dev/sda2            2138        3916    14289817+   7  HPFS/NTFS
/dev/sda3            3917        4865     7622842+   5  Extended
/dev/sda5            3917        4818     7245283+  83  Linux
/dev/sda6            4819        4865      377496   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1457212c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19582   157292383+   7  HPFS/NTFS
/dev/sdb2           19583       24992    43455825    7  HPFS/NTFS
/dev/sdb3           24993       30401    43447792+   7  HPFS/NTFS

the systems are all on the first one, cause the second one is external disk...
now when i see grub i have ubunut and xp to choose from
when i choose xp, then i get a choice (in win7 boot loader) for xp or win7...
i can add link to go directly to win7, i know that...i think it should be like this

> title Windows 7
root (hd0,**2**)
savedefault
makeactive
chainloader +1 			 		

cause i think that the second (dev\sda2) one is for win7, the first one is xp...
but i will still have a choice for both xp and win7 when i go to xp in grub...
i don't know how to fix that...i don't really need to fix it, as long as it works..
but it's good to know how it works, thank you for your guidance and ideas..

---

