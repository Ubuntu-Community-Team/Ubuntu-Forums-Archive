---
title: "Vista -&gt; ubuntu -&gt; XP"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by bessermt on 2009-05-10
I have a new laptop that came with Vista installed.  My old computer has XP.  I tried to install ubuntu 9.04 but now my computer is broken.  Here's some specs if that helps:

300GB HD
3GB DDR2

I thought this would be enough to load all 3 OS's.  I can't seem to get ubuntu to partition ntfs (it's not an option).  My laptop won't take floppies, so I can't use my old fdisk utility.  My XP disks say I don't have a hard drive at all.  My computer never came with Vista disks (but I did create a set of recovery disks using a utility that was on the laptop).  

I've been trying all weekend to do this, but no luck.  Anyone know how to install all 3?  I have even tried to install just 2, but that doesn't work either.  All I get is that I have no hard disk unless I only install ubuntu alone.  I've been reading and reading but nothing suggested in the docs or websites work.  

Help, please.  All my data is gone.

---

### Post by logos34 on 2009-05-10
try shrinking vista first using its own built-in disk utilities.  Then see if ubuntu recognizes it correctly (or if you want triple boot try installing xp next).

good luck

also [this ]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html")might be of help (-->defrag etc)

---

### Post by JK3mp on 2009-05-10
Yeah go to the mycomputer icon, right click manage, then go to disk managment, it allows you to shrink it how ever much it can take and/or you want. THen you'll have free space on the disk to install ubuntu on. :) . Just make sure you set the partitioner on ubuntu to install ONLY to the freespace, or it will delete ALL of it.

---

### Post by Neostar on 2009-05-10
You can also use something like Parted Magic to partition your hard drive into 4 slicers, 1 for each version of Windows and 2 for Ubuntu.

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by bessermt on 2009-05-10
There's no XP on my hard disk to shrink.  Everything is gone.

---

### Post by bessermt on 2009-05-10
Tried to get Partition Magic as suggested.  Just fails to extract.  

All I really want is a good description on how to format my laptop so I can install at a minimum Vista and ubuntu (XP is a nice to have).   Read plenty of ones that don't work, so I'm looking for a good and simple and foolproof way to install on what is now a blank laptop computer.  

While I appreciate suggestions, remember this is an absolute beginners section so please don't suggest something that requires previous knowledge.  That will just be irritating.  

Monday I'm going to contact Microsoft and get a copy of Vista on CD so I can re-install it.  
They should give it to me for free since I already paid for it as part of my laptop purchase.  I'd like to keep ubuntu on here, but if it has to go, so be it.  I have to get work done.

---

### Post by albinootje on 2009-05-10
> **bessermt said:**
> 
Monday I'm going to contact Microsoft and get a copy of Vista on CD so I can re-install it.  


It's possible that your hard disk has a "hidden" Vista recovery partition. And besides that it is easier to first install MS-Windows, and then Ubuntu.

Please boot with an Ubuntu Desktop installation cdrom/dvd/usb-stick, and use "gparted" to look at the partitions, and then also post the output of the following in a terminal :
```

sudo fdisk -l

```

---

### Post by Niniel on 2009-05-11
The best way to install all 3 OSs is, in my opinion, to start with XP, then add Vista so that Vista can set up double-booting with XP, and then add Ubuntu so that Ubunty can set up Grub to double-boot Windows (Vista).
Since you already have Vista, maybe [this guide]("http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm") will help you set up XP next to it (to be followed by Ubuntu).

---

