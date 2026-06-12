---
title: "[NEWB] Installing Ubuntu 8.04 or KUBUNTU 9.04 on a BS fixed HDD"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by dark_prince on 2009-05-26
**Hellow all humans :D**

Sooner, I will be kickign Windows XP outta my computer and installing Ubuntu, but there is a dumb question,

**How can Install Ubuntu on:**

PIII 500 MHz, 320 MB RAM, JN440BX Motherboard with ATi Rage Pro Turbo AGP 2X graphics.

[b]And above all a bad sectored, 40 Gig hard drive having only about 25 Gigs as usable space. The problem of bad sectors is fixed as shown in the following screenshot:
[IMG]http://i41.tinypic.com/107qul1.jpg[/IMG][/b]

It wud be fine if I replace windows Install in my C: Drive to Ubuntu? If i do the full erasing install, I will lose all the data on my HDD (VIP stuff :P) + the bad sectors will come to life too. Currently the partitions I have, work perfect till 99.9% storage :D

[u]Should i just format it under GParted and select it for installation?
or
Is there any other way to do this? (pocket guide doesnt explain that lol)

Preciously I had installed, Mandriva Linux One 2007.1, SLAX, NimbleX (the distro whihc Auto recognizes FAT Partitions)

**2nd Question:** If the installation goes fine, will Ubuntu be auto recognizing and mounting my FAT Partitioned D: Drive? (I dont want to format it)

If not, what changes wud I do in FSTAB ? (I did that after installing mandriva, and it didnt allowed me to remove folders in partition root :( and also i cudnt reformat the partition too)
[/b]
Please reply

Also, I have one Kubuntu 9.04 but it doesnt boot into kde when I use live cd. What shud i do to install that?

When i write sudo startkde or sudo kdm, it doesnt start KDM or KDE, isntead on startkde, it shows a message that display is not configured. If i use xconf or xorgconfig, it clearly states that its not a valid command. Guide me regarding that too.

I feel more easy with KDE, preferably KDE4 since I have used it for about a span of 6 months already back in early 2008.

so many querries?
**Thank you all for ur quick, outstanding suport**

Moeen Mahboob, Pakistan, 44000
P.S an urdu language port wud be nice too :)

---

### Post by halitech on 2009-05-26
if you have that many bad sectors then I would recommend getting a new (new to you) drive as 8gigs won't give you much room to do much. 

as far as the fat drive goes, I believe you will need to edit fstab to get it mounted properly at boot

ati can be a bugger to setup and you have an old card so will be even worse so chances are the live cd won't work and you'll need to use the alt install cd.

---

### Post by peakshysteria on 2009-05-26
> **halitech said:**
> if you have that many bad sectors then I would recommend getting a new (new to you) drive as 8gigs won't give you much room to do much. 

as far as the fat drive goes, I believe you will need to edit fstab to get it mounted properly at boot

ati can be a bugger to setup and you have an old card so will be even worse so chances are the live cd won't work and you'll need to use the alt install cd.

It was a walk in the park to install the ATI drivers on my machine with 8.04 and 8.10. Now running Jaunty which worked out of the box. No need to install the ATI drivers. <before 8.04 and on my old laptop with ATI 9000 card it was a pain. But this should be the least of his problems here. Run the live CD and see how it takes.

---

### Post by dwouters on 2009-05-26
> **halitech said:**
> if you have that many bad sectors then I would recommend getting a new (new to you) drive as 8gigs won't give you much room to do much. 

as far as the fat drive goes, I believe you will need to edit fstab to get it mounted properly at boot

I agree with part of this. 8 gigs will not do you much good. As far as FAT, I believe that once installed, that partition will show up under the "computer" icon on the menu. Ubuntu has not problem at all with NTFS and I will assume the same with FAT. I do not think it will be necessary to edit your fstab.

Anyone is welcome to correct me if I'm wrong here.

---

### Post by Irishe on 2009-05-26
I'm Fairly new to  this but From What i read, i'd suggest purchasing an
external USB hard drive and Copy all the VIP stuff to it through windows.
Once you've backed up all the Files you want to keep, disconnect it and 
use the Whole Drive for your Ubuntu 8.04 install. That 37gb is plenty.
then just go to the Synaptic Manager and install the KDE desktop 
environment. 


Just my 2 cents as i installed ubuntu on a 10 y/o Gateway dual boot with XP pro,
700mghz slot A, 396ram, tnt64 video and it works great on just 40gb.

Good Luck.

---

### Post by dark_prince on 2009-05-26
**1st off:** I cant buy a new storage, thats why the bad sectors are compromised. 8 gigs wud be enough, I will be manually resizing the free space in my D drive for the SWAP partition
**2ndly,** I will happily do the changes in FSTAB (if installation worked)
**3rdly,** Kubuntu 9.04 lvie cd boot correct, no sign of error, but doesnt go into GUI instead into command line. Read my post again about the problem I encountered.

My 1st Question isnt answered yet, which was:
**Can i still reformat my C: drive only as ext3/2 and use it as ubuntu install destination?**

I only have a 2 gigs USB pen drive. I am engineering student and all i have got is my research stuff + setups + Pro-Engineer (6 gigs). All about Mechatronics. I cant risk loss of data and it cant be stuffed into 2 gigs of USB. Moreover, I cant boot ubuntu off my usb since my JN440BX's bios doesnt recognize bootable USB pendrives. Otherwise, I might be following PENDRIVELINUX community's Ubuntu 9.04 persistent install on my flash drive.

**Answer to the last post: READ MY FIRST POST WITH OPENED EYES PLEASE!**

Just answer my simplest question

I will report back after trying booting into ubuntu 8.04 (8.10, I gifted all my 5 CDs to my colleages and frnds :) )

ThanX alot for ur quick help

---

### Post by dark_prince on 2009-05-26
Back!

posting this in Mozilla Firefox from Ubuntu LiveCD 8.04

no sound devices found
VGA Drivers are i think in safe mode (no higher resolution than 800x600 and no higher refresh rate than 60hz)

:( :( looks like I have to eat dust on windows xP again?

didnt tried installation yet.

Sound Drivers: Crystal WDM Audio (on Board sound device on JN440BX)
Graphix: ATi Rage Pro Turbo AGP 2x

---

