---
title: "Can I run Kubunt on my laptop with windows 7?"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by Timo0060 on 2010-11-18
Hello, I have a laptop that came with windows 7 on it already. Is there anyway I can install Kubuntu 10.10 on it without having to re-install windows 7? Currently I'm running Kubuntu on Oracle virtual box, but it's to slow and choppy. Any help would be great. Thanks to anyone who can help

---

### Post by Hippytaff on 2010-11-18
If there is enough room you can dual boot with W7. To see if you have room boot from a liveCD, click install, and when you get to the partition page it will give you an option to either install alongside windows or completely remove windows. If you don't get the option then you haven't got the room (which happend to me).
 
The options then are either shrink the windows partition or carry on with virtual os. :-)

---

### Post by jrev on 2010-11-18
If you want to check the space on your hard disk just put the Ubuntu install CD in your CD reader and restart your PC for a Live-session.
When you come to the desktop open a console via menu ```
Applications/Accessories/Terminal 
```
and then type " sudo gparted "
You will see the size of your hard disk and the number of partitions in use :p
You will then find out how much space is left for Ubuntu and create your new partitions accordingly

---

### Post by Hippytaff on 2010-11-18
> **jrev said:**
> If you want to check the space on your hard disk just put the Ubuntu install CD in your CD reader and restart your PC for a Live-session.
When you come to the desktop open a console via menu ```
Applications/Accessories/Terminal 
```
and then type " sudo gparted "
You will see the size of your hard disk and the number of partitions in use :p
 
Good thinking :-) didn't think of that :-) Doh

---

### Post by Rubi1200 on 2010-11-18
It is very important to also resize the Windows partition using the built-in Disk Management tools in Windows.

It is also advisable to run chkdsk a few times after doing this just to make sure Windows is "happy."

You can create a partition for Ubuntu, but do not format it. Wait, and do it when you install from the LiveCD.

---

### Post by Mark Phelps on 2010-11-18
> **Rubi1200 said:**
> It is very important to also resize the Windows partition using the built-in Disk Management tools in Windows.

It is also advisable to run chkdsk a few times after doing this just to make sure Windows is "happy."

You can create a partition for Ubuntu, but do not format it. Wait, and do it when you install from the LiveCD.

+1 -- really ... it is very important NOT to let the installer shrink the Win7 OS partition.  Doing so can result in Win7 OS corruption, rendering it unbootable.

Also, since the new installer NO LONGER offers the "install to largest free space" option, be VERY CAREFUL when you do the installation.  If you accidentally select the wrong options, you will wipe out your Win7 install.

It would also be a good idea -- BEFORE you do the dual-boot install -- to go into the Win7 Backup feature and use the option to create and burn a Win7 Repair CD.  This will become invaluable later should you need to repair the Win7 boot loader from the dual-boot setup.

---

### Post by Timo0060 on 2010-11-18
I found out you could use wupi to have it run along side with windows 7, but now when i try to update my system, it doesn't download anything.... any help with that? and remember, i'm new to all this, if you name hardware i'll know, but software i have no idea. so help please, if you can. thanks

---

### Post by anewguy on 2010-11-19
Just me personally - wubi = bad idea.  Either continue in a virtual machine or install for dual boot.

I don't know Windows 7, so I don't know anything about the partition shrinking.  However, if you are going to resize the Windows partition to make room for Ubuntu, be sure to run defrag a couple of times in Windows so you can get as much contiguous space as possible without hosing your Windows file system.

Dave ;)

---

