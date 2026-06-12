---
title: "The Tale od ndiswrapper and Ubuntu wireless hell (a.k.a., HELP ME)"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by Ryan Cacophony on 2007-09-03
Well, I've been trying to get wireless working on my linux partition since ubuntu 6.?? now.  Every weeekend or so, I boot over and see if maybe I can do something right this time.   But it never works, and my computer is useless to me without it's wireless internet due to the fact that it's a desktop, and located across the house and up a flight of stairs from the wireless router (ie. It's intractable to _not_ use wireless).  So Finally, I come here for help.

I have a Dell Wireless 1450 USB adapter

It has some sort of broadcom chipset

I have the original drivers.  In the folder with the driver has the following files:
DELLNIC.inf
DELLNIC.cat
PRISMA02.sys
CoPrism.dll

I have the Ubuntu 7.04 Live disk, with this, I have Ndiswrapper

I once had mandriva with ndiswrapper with a graphical interface, and I somehow dot my wireless to work by clicking buttons until it somehow *magically* worked.

As far as I can see, ubuntu doesnt even recognize the device.  It plugs into a straight up usb hub.

I can install the ind file fine, but ndiswrapper does not claim that the hardware is present.

I have to boot over to windows in order to get onto the internet at all.  This is a royal pain in the *** for solving issues, but I have no problem doing this slowly over a few days.  If I need something to be installed, I do have the ability to download it in windows, put it on a flash drive, and then install it in Ubintu that way, if possible.

Please help, I'll post anything else that you need.

---

### Post by Ryan Cacophony on 2007-09-04
Ive been sent back three pages with no reply...... please help?

---

### Post by cagey cretin on 2007-09-04
What happens when you open up device manager? (System -> Administration -> Device Manager) Do you see your wireless card listed?

If so, open up Networking (System -> Administration -> Networking) and see what your wireless properties are: is it activated (try clikcing activate)? If not check properties (are you using the correct key - ascii or hex?). Are you set to accept DHCP? 

I got some help from bmartin pointing me to WICD as a wireless manager, so if we can get your card recognized, take a look at that (that thread is [[color=red]here[/color]]("http://ubuntuforums.org/showthread.php?t=538613").

---

### Post by kevdog on 2007-09-04
Please post the following and I can help you -- ndiswrapper and your card should not be any type of problem.

lshw -C network
lspci -nn

Also, you should probably install ndiswrapper from source and not repository.  I have directions how to do this.

---

