---
title: "installation"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by vijayrajuu on 2010-06-13
hey there!! i m new to the ubuntu community but have heard a lot about the OS an a lot of friends have recommended it to me.. but unfortunately i can't install the OS on my internal hard drive.. i am looking to install the whole xubuntu OS on a 4gig usb drive.. will this work? if yes what are the steps? any help would be appreciated..

thanx in advance.. :)

---

### Post by garvinrick4 on 2010-06-13
I do believe on your install disk for ubuntu you can use " choose try Ubuntu and not install." Now go to System to Administration and choose "Startup Disk Creator" open it
and choose your downloaded .iso file that you downloaded. Now be sure and pick your
USB drive and slide the slider over to 4 gig of persistence and start making a USB drive
that holds your 4 gig. Takes about 3.5 or so to load your system after install so you are cool and can be used as a LIVE USB.

Three things to do in startup disk creator make sure you get them right. Your iso file to install, your usb drive to install in and slide the slider over to the far right at 4 gig.
If you do not have an .iso file of what you want to install. Go to the web site and download the version of Ubuntu that you want to desktop that is your .iso file. Take about
15 minutes and is 699 meg or so. If you do not have a CD take that file and BURN a CD first.

---

### Post by -kg- on 2010-06-13
As an addendum:

4GB is just ***barely*** enough for an installation.  You won't be able to do much with it.

It would be nice if you could get at least an 8GB USB drive.  Larger is better...16GB would be twice as nice! :p

8GB would give you a fairly operable installation, though you wouldn't have room to do much with it.  16GB would give you sufficient room to do a few things, and install some additional software that you might want to check out.

BTW:

> ...unfortunately i can't install the OS on my internal hard drive...

Why not?  Is it choice, size constraints, or something else?  Maybe we could help.

---

### Post by garvinrick4 on 2010-06-13
If you use a large USB drive and install Ubuntu on it you will get a new grub installed over your exsisting windows boot manager. If you use startup disk creator the USB drive will not effect your boot process. 
  Having a system that can hold a bit of a Home folder is nicer but understand grub2 before you play with Linux on USB drives. Optimum is what -kg- mentions is a dual boot for your machine. Start with what makes you feel secure. Always remember your drive and its boot manager will look at a Ubuntu install like another hard drive and the boot manager comes with that. The only exception are LIVE USB or CD's. You got a 4 gig right now give Ubuntu a shot with startup disk creator is a nice way. Here is a nice file to download with how to use Ubuntu.. And one with a manual for whatever version you choose to use.

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[Main Page -]("http://ubuntuguide.org/wiki/Main_Page")

---

### Post by -kg- on 2010-06-14
> If you use a large USB drive and install Ubuntu on it you will get a new grub installed over your exsisting windows boot manager.

One word:  [UNetbootin]("http://unetbootin.sourceforge.net/")

---

