---
title: "Ubuntu Won't install, get a black screen"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Anhslaught on 2008-12-22
Ok, well I've so far tried Ubuntu 8.04-8.10 and none of those work.  I can't seem to find Ubuntu 7.10 anywhere.

Materials I'm  using
-----------------------------------
Linux 8.10 32bit Version and 64bit version ISO on main page
Linux 8.04 32bit version and 64bit version ISO on main page
Lightscribe DVD burner with light scribe discs

My system:
ASUS RAMPAGE FORMULA LGA 775 Intel X48 ATX Intel Motherboard
Intel Core 2 6600 Quadcore
4g OCZ ram 5-5-5-3
Asus ATI Radeon 4850
300g WD VelociRaptor Hard Drive

I got Windows XP SP3 installed on my C drive.  I partitioned 100 gigs for my D drive as reservation for Linux.

That's all the info I can think of right now.


Problem:
----------------------------------
So about my problem.......

For all those discs that I've made, I've gone through the same process with the same conclusion.  I get an Ubuntu logo loading, which brings me to the menu for types of installation selection
ie. Install Linux/Memory Check/Disc Check/Demo

I've done both Demo and Installation and it brings me to this Ubuntu loading screen which takes about 5-8 minutes.  After the 5 to 8 minutes, I get to this black screen and it stays there black and then my monitor goes off, then the black screen appears again.  The process repeats.  I don't get any further than that.   

SO, is this an incompatibility problem?

---

### Post by Thameslink on 2008-12-22
> **Anhslaught said:**
> Ok, well I've so far tried Ubuntu 8.04-8.10 and none of those work.  I can't seem to find Ubuntu 7.10 anywhere.

Materials I'm  using
-----------------------------------
Linux 8.10 32bit Version and 64bit version ISO on main page
Linux 8.04 32bit version and 64bit version ISO on main page
Lightscribe DVD burner with light scribe discs

My system:
ASUS RAMPAGE FORMULA LGA 775 Intel X48 ATX Intel Motherboard
Intel Core 2 6600 Quadcore
4g OCZ ram 5-5-5-3
Asus ATI Radeon 4850
300g WD VelociRaptor Hard Drive

I got Windows XP SP3 installed on my C drive.  I partitioned 100 gigs for my D drive as reservation for Linux.

That's all the info I can think of right now.


Problem:
----------------------------------
So about my problem.......

For all those discs that I've made, I've gone through the same process with the same conclusion.  I get an Ubuntu logo loading, which brings me to the menu for types of installation selection
ie. Install Linux/Memory Check/Disc Check/Demo

I've done both Demo and Installation and it brings me to this Ubuntu loading screen which takes about 5-8 minutes.  After the 5 to 8 minutes, I get to this black screen and it stays there black and then my monitor goes off, then the black screen appears again.  The process repeats.  I don't get any further than that.   

SO, is this an incompatibility problem?

I've been having similar promblems with a ati sapphire 9550 but I can boot it in safe mode (f4 on menu) from the live cd, but after install & update it wont boot in safe mode from grub for either kernel.
After ubuntu bar fills up screen goes blank.

Any ideas anyone?

---

### Post by mikeyphi on 2008-12-22
This guide has previously been suggested in the forums:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by Kevbert on 2008-12-22
Welcome to Ubuntu.
The ATI 4850 is quite a new card. In the boot options it may be worth adding vga=791 or something similar to force the display to a certain resolution. More info can be found [COLOR="Red"][here]("https://help.ubuntu.com/community/BootOptions")[/COLOR].

---

