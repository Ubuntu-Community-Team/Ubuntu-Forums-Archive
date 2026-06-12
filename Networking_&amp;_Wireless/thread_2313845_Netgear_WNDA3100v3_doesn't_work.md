---
title: "Netgear WNDA3100v3 doesn't work"
date: 2016-02-16
forum: Networking &amp; Wireless
---

### Post by pimdegreef on 2016-02-16
I've installed the drivers, run lsusb and it showed up but ndisgtk tells me there is no hardware connected. Well, it is. 

I've both installed the 32 and 64-bit driver but it doesn't work.

---

### Post by chili555 on 2016-02-16
If you cannot and will not buy a supported device because you love pain and frustration, then let's proceed.

Please insert the device and then run and post:```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
```Where did you get the drivers? ndiswrapper only works with XP and, rarely NT, drivers appropriate to your architecture; either 32- or 64-bit. If you have anything else, like a bad tooth, they will have to come out!

DISCLAIMER: ndiswrapper is tricky, stubborn and a crutch. Sometimes it works well and sometimes, despite our best efforts, not at all.

---

### Post by pimdegreef on 2016-02-16
Thank you for your time, I'll buy a other one...

Okay, let's try...

pim@pim-desktop:~$ ndiswrapper -l
bcmn43xx32 : driver installed
bcmn43xx64 : driver installed

pim@pim-desktop:~$ dmesg | grep ndis
[   26.120140] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   26.120917] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   27.125415] usbcore: registered new interface driver ndiswrapper
[ 1171.978579] usbcore: deregistering interface driver ndiswrapper
[ 1171.986781] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 1171.996254] usbcore: registered new interface driver ndiswrapper
[ 1177.462183] usbcore: deregistering interface driver ndiswrapper
[ 1177.468812] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 1177.477807] usbcore: registered new interface driver ndiswrapper
[ 9485.349574] usbcore: deregistering interface driver ndiswrapper
[ 9485.360600] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 9485.373732] usbcore: registered new interface driver ndiswrapper
[ 9514.878351] usbcore: deregistering interface driver ndiswrapper
[ 9514.886873] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 9514.893997] usbcore: registered new interface driver ndiswrapper
[ 9538.283187] usbcore: deregistering interface driver ndiswrapper
[ 9538.291697] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 9538.302599] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2016-02-16
Your *ndiswrapper -l* doesn't report that the device is present because the inf file you loaded doesn't have the matching usb.id. I suspect you have drivers for a V1 or a V2; you say yours is a V3.

As well, you needn't have the 32-bit and the 64-bit drivers loaded, you need drivers appropriate to your architecture; _either_ 32- _or_ 64-bit.

Let's erase everything you have so far and start fresh:```
sudo ndiswrapper -e bcmn43xx32
sudo ndiswrapper -e bcmn43xx64
```Now run and post:```
lsusb
arch
```We'll find the right drivers and install them.

---

### Post by pimdegreef on 2016-02-17
> **chili555 said:**
> Your *ndiswrapper -l* doesn't report that the device is present because the inf file you loaded doesn't have the matching usb.id. I suspect you have drivers for a V1 or a V2; you say yours is a V3.

As well, you needn't have the 32-bit and the 64-bit drivers loaded, you need drivers appropriate to your architecture; _either_ 32- _or_ 64-bit.

Let's erase everything you have so far and start fresh:```
sudo ndiswrapper -e bcmn43xx32
sudo ndiswrapper -e bcmn43xx64
```Now run and post:```
lsusb
arch
```We'll find the right drivers and install them.

pim@pim-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer
Bus 002 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 006: ID 24ae:2000  
Bus 003 Device 007: ID 248a:88a1  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 012: ID 0846:9014 NetGear, Inc. 
Bus 006 Device 002: ID 046d:0819 Logitech, Inc. Webcam C210
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

pim@pim-desktop:~$ arch
i686

If I try to use the original v3 driver it says it is a bad driver or something.

---

### Post by chili555 on 2016-02-17
This thread gives you a very good explanation: [http://ubuntuforums.org/showthread.php?t=2291817](http://ubuntuforums.org/showthread.php?t=2291817)

Also, check here: [https://wikidevi.com/wiki/Netgear_WNDA3100v3](https://wikidevi.com/wiki/Netgear_WNDA3100v3)> Probable Linux driver
unknownUnless you can find 32-bit *XP* driver files, we are stuck.

---

