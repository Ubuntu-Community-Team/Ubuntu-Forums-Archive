---
title: "Netgear WN121T set-up method for Xubuntu 8.04 not working in Ubuntu 8.04"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by jaredudu on 2008-07-23
Hi, Im very new to Linux as I have just switched over from Windows for good :)

The only problem I am encountering is that my Netgear WN121T will not configure correctly. I have attempted work arounds with ndiswrapper in Xubuntu and have had success but I cannot say the same in regular Ubuntu.

[IMG]http://img184.imageshack.us/img184/316/screenshotjaredjareddesiq9.png[/IMG] (Please ignore the not so great screenshot)

This is the method I used > I was using this adapter in Mepis 6.5 and I could install it quite easily, but with PCLOS I could never get it work (that was the reason why I tried Mepis) until this afternoon.

There are no Linux drivers for this chipset, so you are forced to use Ndiswrapper. Using the PCLOS control center I always get to the point that it asks me the location of the inf file, it installs the driver, but then an error message tells you that there are no wireless interfaces for the device.

In the end I've decided to remove Ndiswrapper, install the last stable version (1.51) and proceed as described on the website using the command line. However, according to the wiki older versions than the one in the repos support this driver. I'll try and tell you later.

First of all, I've downloaded the TopDog driver for Windows XP from this address:



[http://download.opendrivers.com/showfile.php?file=/network/marvell/topdog_drv10049.exe](http://download.opendrivers.com/showfile.php?file=/network/marvell/topdog_drv10049.exe)



It's a self-extracting zip archive. While the drivers coming with the installation CD comprise a .inf a.sys and a.cat file, these contain just the .inf and the .sys file. My motto is "The simpler, the better".



Install the driver with:



ndiswrapper -i /"location of the inf file"/netmw245.inf



then type



modprobe ndiswrapper



at this point the light on the device should switch on and a new interface should be created. You can check it with



iwconfig



Once done this, you can run the PCLOS Control Center and configure it graphically.



Now everything is working.

Please help Ubuntu gurus!

---

