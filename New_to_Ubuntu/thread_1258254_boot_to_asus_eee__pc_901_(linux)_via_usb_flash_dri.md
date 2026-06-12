---
title: "boot to asus eee  pc 901 (linux) via usb flash drive"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by bubbleoffplumb on 2009-09-04
trying to boot Ubuntu (netbook version) from usb flash drive onto asus eee pc 901 (linux)


I used my imac (os x 10.5.7)
to download the img file - followed instructions and I think it's on the usb flash drive.

when I plug into my mac and click on it:

[B]autorun.inf
casper
dists
install
md5sum.txt
pics
pool
preseed
README.diskdefines
syslinux
wubi.exe
[/B]
I found this "jaunty" folder under dists folder:

[B]main
multiverse
Release
Release.gpg
restricted
universe[/B]

I assume this means jaunty is on there.
so It's only a matter of getting the asus to cooperate??

or am I totally in the dark here??

.... on to the asus
at one point, I put the usb in (asus) and hit escape

two sandisc cruzer (usb) options come up - the first:

**boot error**

the second:
[B]Intel UNDI, PXE-2.1 (build 082)
Copyright (c) 1997-2000 Intel Corporation
For Atheros AR8121/AR8113 PCIE Ethernet Controller v1.0.0.4 (2008/01/13)

CLIENT MAC ADDR: 00 23 54 3C )D AF
Check cable connection!
PXE-M0F: Exiting Intel PXE ROM.

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key
[/B]
(after I press a key)
**boot error**

---------

can anyone assist? - what do I need to do to get this goin' on the asus?
:confused:

my original thread:
[http://ubuntuforums.org/showthread.php?t=1257468](http://ubuntuforums.org/showthread.php?t=1257468)

eta:
BIOS version: 0607
BIOS date: 09/24/2008
Softwasre version:
Eee PC 1.6.1.3
Build Info: 2008-08-06 05:53
CPU type: Intel (R) Mobile Processor
Memory size 1024 MB
Motherboard version x.xx

---

### Post by achianese on 2009-09-04
I'm not an expert, but I have used a Sandisk Cruzer to install Ubuntu on an eeePC, 1000HE.

Just taking a stab here, but it might be the case that your Sandisk still has the U3 partition that comes with these drives for auto-run functionality. Hence the two boot devices..  One is the main drive and the other pretends to be a CD so Windows will autorun it. I removed mine using a util provided by Sandisk. I don't know if this will work for you, but it might be worth a shot, especially if you don't use U3.

I googled Sandisk U3 removal mac and found this:

[http://communities.sandisk.com/sandisk/board/message?board.id=u3&thread.id=1066](http://communities.sandisk.com/sandisk/board/message?board.id=u3&thread.id=1066)

---

### Post by achianese on 2009-09-04
p.s. You would have to run the util, then re-image the USB drive, I imagine.

---

### Post by bubbleoffplumb on 2009-09-05
thank you achianese.
 I think I was successful with getting that u3 stuff off the flash drive, and I'm in the process of putting the img file on again.
I'm in terminal and got "no such file or directory"
noticed that the file name ends in img.part
what's .part??
is something wonky causing this not to see the file?

---

### Post by bubbleoffplumb on 2009-09-05
silly me
I'll have to wait a bit and try again.
I noticed way down at the bottom of the page  - active download.
it's not finished yet.
it'll be done in about 15 mins and I'll try it again.

thank you for giving me something to try.

---

### Post by LewRockwell on 2009-09-11
information regarding netbooks and compatability:

[https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks](https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks)

.

---

