---
title: "basic wubi question"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by degarb on 2010-03-04
Would you be able to use wubi if your windows xp got corrupted one day when you turned on the machine?  (I am thinking off adding ubuntu to main desktop as a backup to xp, but not ready to partition drive before navigating all bugs to see if practical.)

Also, do these grub installers play well with the multibooter of xp.  I already have two xp installations and a boot chooser at the start,  I am not sure is xp old is up to snuff and works anymore.  I would hate to try wubi and it choose only the old xp install for the boot choice screen.

---

### Post by earthpigg on 2010-03-04
> Would you be able to use wubi if your windows xp got corrupted one day when you turned on the machine?

maybe, maybe not. it depends on what, exactly, in windows gets corrupted. i wouldn't count on it, though.

> Also, do these grub installers play well with the multibooter of xp. I already have two xp installations and a boot chooser at the start, I am not sure is xp old is up to snuff and works anymore.

wubi doesn't use GRUB, it uses the windows multiboot thing. i would assume that wubi will simply add it's own entry to the two already listed, but i've never tried it so can't speak from personal experience.

---

### Post by undecim on 2010-03-04
Grub should play fine with the bootloader. The only thing is that when you choose to load Windows from grub, it will load the windows boot chooser for you to choose a windows XP installation to boot. (in other words, you have two menus to go through)

If you are going to use Ubuntu as a backup, you need to do a regular install, rather than use Wubi. If the file where Wubi stores its information gets botched, then you won't be able to use Wubi. So like earthpigg said, it depends on exactly what goes wrong with Windows.

Partitioning really isn't difficult. The Ubuntu installer will do it for you and all you need to do is decide how much space to allocate to Ubuntu.

---

### Post by degarb on 2010-03-04
I am guessing there is not any windows gparted.  And last I checked, there was no freeware version of a repartitioning tool that was user friendly.  And if it isn't clear what you are doing you could screw up the drive.   A good free tool needs to be clear like gparted or partition magic.  This is a one shot tool that is used every 5 years or so by an OP.  And so, there really is no logic in any not straight forward tools for this.

And if you slice off a piece of a harddrive, and then decide to reunite that piece later, you need a free gparted for windows.

---

### Post by earthpigg on 2010-03-04
> **degarb said:**
> And if you slice off a piece of a harddrive, and then decide to reunite that piece later, you need a free gparted for windows.

gparted isn't a windows program, but it can be used 'for windows'. you can either get a dedicated gparted livecd, or just use any old ubuntu live cd.

[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

see #9, skim/read both links.

and, as always, it is important to back all of your important data up before you partition.

---

### Post by wgilbert5 on 2010-03-05
I run Ubuntu 9.10 on my eee netbook in wubi on XP right now and have no problems so far.  As a matter of fact I haven't run XP in quite a while and use it almost 100% as a Ubuntu machine.  Its true that you have to make the choice at startup of which OS to run and, once again it will ask you for a choice.  Once you do that, its just like running on my desktop right here.  Try it and I'll bet you end up in Ubuntu more than XP!  All the best, Bill

---

### Post by degarb on 2010-03-07
I got an external 500 gig usb drive, in addition to the more limited internal drives.  Could this external drive be used for both the wubi and regular install drive?

---

### Post by candtalan on 2010-03-07
> **degarb said:**
> I got an external 500 gig usb drive, in addition to the more limited internal drives.  Could this external drive be used for both the wubi and regular install drive?

1) With wubi the boot loader is the Windows boot loader, controlled by win.ini. If the external drive was used with wubi install then the external drive was removed one day, then my guess is that windows would boot ok and all would be normal except you have no ubuntu facility.

2) However, with a conventional install, the boot loader is grub (linux) and the files are located in the installed Ubuntu partition. The MBR is converted to point to the linux grub files. So if the external drive disappears one day, you will not be able to (easily) boot windows, which you might find inconvenient.... 

It is better to use a permanently fixed drive for installs. 

Even with 2) above, it is easy to fix the mbr if you know how, and are prepared for it, so no big deal really.
hth

---

### Post by degarb on 2010-03-07
> **candtalan said:**
> 1) With wubi the boot loader is the Windows boot loader, controlled by win.ini. If the external drive was used with wubi install then the external drive was removed one day, then my guess is that windows would boot ok and all would be normal except you have no ubuntu facility.

2) However, with a conventional install, the boot loader is grub (linux) and the files are located in the installed Ubuntu partition. The MBR is converted to point to the linux grub files. So if the external drive disappears one day, you will not be able to (easily) boot windows, which you might find inconvenient.... 

It is better to use a permanently fixed drive for installs. 

Even with 2) above, it is easy to fix the mbr if you know how, and are prepared for it, so no big deal really.
hth


Logical.  It seems that 2) is a big downside to using ubuntu.

I am not really comfortable making the entire OS a single file, that on one power outage, entire install could be wiped with one bit getting a bad write.  Okay for a test, but not day to day run.    And, I am not soon to install ubuntu on internal drive for space reasons.

Shame to see grub limiting ubuntu to primary drive.  It has been decades since i messed directly with mbr, and don't recall anything of it.   What are you referring to?

---

### Post by sandyd on 2010-03-07
you can create a persistant installation of ubuntu on your 500 gb drive. if your computer is new enough, it will have a "usb boot" option that allows you to boot from the 500 gb drive instead of the hard disk.

---

### Post by candtalan on 2010-03-07
> **degarb said:**
> It seems that 2) is a big downside to using ubuntu.

No so! this dicussion is about an EXTERNAL, removable drive (say USB). You can put the grub stuff anywhere you want, but this needs more thought. 

> 
I am not really comfortable making the entire OS a single file, that on one power outage, entire install could be wiped with one bit getting a bad write.  Okay for a test, but not day to day run.

Wubi is not so robust, but is great for a short time test. Also easy to remove.

> 
And, I am not soon to install ubuntu on internal drive for space reasons.
Can you add another drive in the machine? Most of my PCs have three drives. Even in an ancient PC with a bios that could not cope with large HD I used a small 50MB partition to carry the grub files, and added a huge modern HD as a second HD. There is a lot of flexibilty.

> 
Shame to see grub limiting ubuntu to primary drive.  It has been decades since i messed directly with mbr, and don't recall anything of it. What are you referring to?
Grub does not limit to primary drive. Windows tends to do that, not grub.

What I say in 2) is that if you make an installation onto a drive, then you will have to keep that drive in place in future because the system will depend upon it.

This is thinking of a beginner, default installation type. There are many ways to crumble to cookie. GNU/Linux is very flexible indeed.

For example I use a asus 900 netbook it has 3 operating systems on it and I can also run from live USB sticks too. One OS is in an SD card, which I leave in place.

---

### Post by degarb on 2010-03-07
> **carlee said:**
> you can create a persistant installation of ubuntu on your 500 gb drive. if your computer is new enough, it will have a "usb boot" option that allows you to boot from the 500 gb drive instead of the hard disk.

I don't remember the exact age, when ever 3 gighz single core cpu's were sold.  I think 2005.   That option in bios sounds familiar.
 
So,  I guess this brings on the question: what happens if the usb drive breaks (what could we do to then get it to boot from regular harddrive.)

This solved, and we would have a really bullet proof system, short of a power supply failure. 

No more freaking out when xp won't boot and must need immediate reinstall (sometimes repair won't work) and all applications reinstalled.  If you rely on a computer for school or work, you can imagine the terror.

---

### Post by Mark Phelps on 2010-03-08
> **degarb said:**
> I am guessing there is not any windows gparted.  And last I checked, there was no freeware version of a repartitioning tool that was user friendly.  And if it isn't clear what you are doing you could screw up the drive.   A good free tool needs to be clear like gparted or partition magic.  This is a one shot tool that is used every 5 years or so by an OP.  And so, there really is no logic in any not straight forward tools for this.


Well, I don't know how you "checked", but if you Google for EASUS Partition Master, you will find a FREE tool that works much like Partition Magic.

---

### Post by degarb on 2010-03-08
> **Mark Phelps said:**
> Well, I don't know how you "checked", but if you Google for EASUS Partition Master, you will find a FREE tool that works much like Partition Magic.


I also didn't know that gparted had a live iso.

Anyone know which is safer or better?

Gparted just has a cooler name.  Easeus just sounds like a sneeze to me.

---

### Post by Mark Phelps on 2010-03-09
> **degarb said:**
> I also didn't know that gparted had a live iso.

Anyone know which is safer or better?

Gparted just has a cooler name.  Easeus just sounds like a sneeze to me.

Gparted works best on Linux filesystems.

EASUS works on Windows file systems.

---

### Post by Silvertones on 2010-03-09
I did a Wubi install about 8 weeks ago. I did all of my basic learning and messing up. When I thought I was ready all I had to do is use add/remove programs and it was gone. Then I did a real side by side install. It was a snap. just as easy as a wubi install. Let the installer do it. Just answer the basic questions

---

### Post by degarb on 2010-03-09
> **Mark Phelps said:**
> Gparted works best on Linux filesystems.

EASUS works on Windows file systems.


I just downloaded what I think is easus partion master.  But it is not an iso, rather installer.  This doesn't seem right.

---

