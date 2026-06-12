---
title: "trouble installing netgear usb wg111v3 wireless adapter on 7.04"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by radtek on 2008-01-16
I'm having trouble trouble installing netgear usb wg111v3 wireless adapter on 7.04. Tried another couple of suggestions from prior threads but to no avail. lsusb shows the device but nothing else.

Help....!

---

### Post by Hightide on 2008-01-18
Have you seen this thread?  It may help

[http://ubuntuforums.org/showthread.php?t=652910](http://ubuntuforums.org/showthread.php?t=652910)

:)

---

### Post by clsgis on 2008-01-18
> **Hightide said:**
> Have you seen this thread?  It may help

[http://ubuntuforums.org/showthread.php?t=652910](http://ubuntuforums.org/showthread.php?t=652910)

:)

That thread shows how to install ndiswrapper on 7.04, where you have to compile it as on Debian 4.0.

I just installed a generic 802.11b device on Ubuntu 7.10.   You don't have to compile ndiswrapper any more.  Just install it (ndiswrapper-utils-1.9) and load the .inf and .sys (and whatever else came with the device) files into it.  The device came with a CD with a /Drivers/WindowsXP folder.  I copied the contents of that folder to the Desktop.  Then

[FONT="Courier New"]sudo su -
cd /home/winston/Desktop
ndiswrapper -l
ndiswrapper -i rtl8187b.inf
ndiswrapper -l
modprobe ndiswrapper
iwconfig
ifconfig -a
dhclient wlan0[/FONT]

and it works.  No more installing kernel source and compiling.  Of course if you don't want to type [FONT="Courier New"]sudo su -[/FONT] you can just precede every one of those commands with [FONT="Courier New"]sudo[/FONT].

---

### Post by radtek on 2008-01-19
Thanks Hightide!!! That did the trick except the drivers used were wg111v3.inf  I knew I just needed to get the right advice on how to do it. I wasn't looking forward to a fresh install.

Mucho Kudos to Hightide and Erwin Criddle.

Now how to tweek it...? It seems kinda slow on the band width side.

---

### Post by halucinations on 2008-01-19
Got mine working. Its on 7.10 (Gutsy) But maybe it will work for you

[http://ubuntuforums.org/showthread.php?t=671935](http://ubuntuforums.org/showthread.php?t=671935)

---

