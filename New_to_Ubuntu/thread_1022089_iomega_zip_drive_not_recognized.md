---
title: "iomega zip drive not recognized"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by vidyadhara on 2008-12-26
I have an ancient 250 mb iomega parallel port zip drive.


my /etc/modules file is the following.

-----
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

sg
ppa
fuse
#lp
----

I switched around the sg and the ppa a couple of times in this file. and rebooted.

Nothing I do seems to bring up the zip drive or any sign of it in the /dev/ directory.

or in /var/log/messages 
or in dmesg messages

each time I reboot my machine with the zip drive powered up and connected to the parallel port.

Should I not bother about this ancient technology anymore.

I was going to give it away as charity. But these folks will have to run windows to use it cant use it on linux without making it work in the first place.

I am running ubuntu 8.04
the ppa module is loaded as is the sg module.

messages for sg module.
----
[   13.939524] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.939529]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   13.966362]  sda1 sda2
[   13.967142] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.974395] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.974421] sr 1:0:0:0: Attached scsi generic sg1 type 5
--------------

messages for ppa module
--------
[   35.077749] ppa: Version 2.07 (for Linux 2.4.x)
---------------------

---

### Post by Kellemora on 2008-12-26
Hi Vid

Some of the early externals required a driver program for them to be recognized, even on Windows machines.

I have a couple of fairly recent Maxtor USB drives not recognized on Ubuntu also, tried moving them back to a different Windows machine and had to download the drivers for it from Maxtor to even get Windows to know it was there.  Then I found drivers for it for Ubuntu so now one of them is working on Ubuntu just fine!

It might not hurt to do a web search using the model number of your zip drive along with Ubuntu and/or Linux to see if anything pops up.  Use something like Google or DogPile for the search, not the search here, it misses a LOT of things.

TTUL
Gary

---

