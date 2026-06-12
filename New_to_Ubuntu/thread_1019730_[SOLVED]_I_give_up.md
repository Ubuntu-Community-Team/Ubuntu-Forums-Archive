---
title: "[SOLVED] I give up"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by garrydog on 2008-12-23
Been trying to sort out a problem for two days now ,i can only get a blank screen on ubuntu .I have been told that it is a problem with the ATI card driver I have tryed to fix it but have failed .


I have two copies of ubantu and windows xp on my hard drive ,will someone tell me how to unistsll the two ubantu copies .As i want to stick to windows only .
Thanks David .

---

### Post by Sjums07 on 2008-12-23
reinstall win and format all the hdd? :D or should it be done without formatting? :D

---

### Post by nerdking on 2008-12-23
should install windows and format the whole drive

---

### Post by mkvnmtr on 2008-12-23
You can boot the live ubuntu disk. Find the partition manager. It will be in system/ admin. That is GParted. With that tool you can delete your linux partitions and leave free space. Then with what ever tool windows has you can enlarge you windows partition. It would be foolish to reinstall when it is so easy to do with the disk.

---

### Post by Elfy on 2008-12-23
fix the mbr first with your win disc then remove the buntu partitions

---

### Post by Duck2006 on 2008-12-23
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by shredder12 on 2008-12-23
well if you can use this link to safely uninstall ubuntu from you system...
[http://users.bigpond.net.au/hermanzone/p18.htm](http://users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by jleewach on 2008-12-23
windows disk inserted, cmd prompt, enter Bootrec.exe /fixmbr, once Windows starts up, use disk management utility to delete Ubuntu partitions & extend your Windows partition to fill the gap. Something like that :)

--Ignore all the above, these are directions for Vista. My apologies--

---

### Post by Elfy on 2008-12-23
> **jleewach said:**
> windows disk inserted, cmd prompt, enter Bootrec.exe /fixmbr, once Windows starts up, use disk management utility to delete Ubuntu partitions & extend your Windows partition to fill the gap. Something like that :)

That's for vista I thought - thread is about XP

---

### Post by anewguy on 2008-12-23
*PLEASE* follow duck2006's advice - I wrote that how-to after many frustrating times of going to dual boot, removing it, going back to dual boot, etc., until I got what I wanted.  The procedure in the how-to is VERY easy, and you'll save some headaches if you follow it. The first step downloads a program that "fixes" your MBR so Windows will boot, THEN the rest walks you through removing the Ubuntu partitions if you want and extending your Windows partition again.  On your first boot to Windows, IF you resized your Windows partition up again, it will either automatically run the disk check or you should request it to.  This just gets the technical "stuff" inside your Windows partition all in sync again.

Dave :)

---

