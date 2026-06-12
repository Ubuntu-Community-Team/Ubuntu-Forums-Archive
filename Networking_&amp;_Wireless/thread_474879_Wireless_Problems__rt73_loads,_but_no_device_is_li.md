---
title: "Wireless Problems : rt73 loads, but no device is listed"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by rectagonal on 2007-06-15
I am attempting to install Xubuntu onto a PowerMac, and get it onto a wireless network using a usb dongle. The dongle is a ralink chipset and has worked in OS 10.4 previously.

On a fresh install of xubuntu the dongle war recognized, as device rausb0. HOWEVER both ifup and dhclient would lock up the computer instantly. I found this bug report : [https://bugs.launchpad.net/ubuntu/+bug/34902](https://bugs.launchpad.net/ubuntu/+bug/34902) and tried many of the recommendations there . I added the DisableIRQ option to my xorg.conf file, and added irqpoll to my yaboot.conf (and ran ybin -v) but the problems persisted. I also tried manually configuring it in /etc/network/interfaces , as mentioned in the bug's comments but this simply lead to my system freezing at boot.

I then removed my changes from /etc/network/interfaces and followed this guide : [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) Everything went swimmingly well untill step 12. As far as I can tell, rt73 is loaded correctly and appears in lsmod, but does not create any wireless device. iwconfig does not report any wireless devices, and ifconfig only shows my built in ethernet. I tried manually adding the mac address of the wireless adapter to iftab, but that has failed to produce any results.

I am out of ideas, any help would be appreciated. I have attached the output of both dmesg and lsmod.

Powermac G4 AGP
Xubuntu 7.0.4
Kernel 2.6.20-15-powerpc

Wireless Dongle : ASUSTek WL-167g USB WLAN Adapter

---

### Post by rectagonal on 2007-06-15
Well the rt73 is the wrong chipset...

My dongle uses the rt2570 chipset. I tried both the 1.1.0b2 driver and the cvs driver from here - [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

Both lock up my machine on modprobe...

---

### Post by rectagonal on 2007-06-17
Just to recap.. in case anyone can provide any sort of expertise to the problem.. I am trying to get a mac online in Xubuntu using a WiFi USB dongle. The dongle is recognized out of the box on Xubuntu 7.0.4 . However any attempt to ifup or run dhcplient on the device results in immediate system freeze.

Relevant details are : 
Powermac G4 AGP
Xubuntu 7.0.4
Kernel 2.6.20-15-powerpc
Wireless Dongle : ASUSTek WL-167g USB WLAN Adapter, rt2570 chipset

I have tried enabling certain options in my xorg.conf , and in my yaboot.conf to prevent irq conflicts as described in this bug here : [https://bugs.launchpad.net/ubuntu/+bug/34902](https://bugs.launchpad.net/ubuntu/+bug/34902) But this has resulted in no help what so ever. 

At this point I mucked around with a cvs build of the rt73 driver for some reason, even though it did not match my chipset. I realized my mistake and removed it.

I did a clean install and the original problem persisted.

I then tried blacklisting all ralink/serialmonkey drivers, and hand compiled both the 1.1.0b2 and cvs drivers for the rt2750. Both drivers lock up the system on modprobe.

I had hoped to try out the rt2x00 driver, but it is only for kernels post 2.6.22. I tried doing a clean install of ubuntu 7.10 desktop PPC so I would be running on such a kernel, however it booted to the busybox shell after failing to get far in the boot process. I tried from two different cd-rs the second burned at a low (4x) speed but that problem persisted.

Hopefully someone can give me some advice as to how to proceed..

Is there a way to do this short of recompiling my kernel ? I did not see the kernel sources as a package on the cd to install..

---

### Post by prairie_dad on 2007-07-24
and I have substantially the same problem, too.  The odd thing is that the same Ubuntu version, that is 7.04, accepts my 2570 based dongle (from AddLogix) on an ancient PC but not my G4...

---

