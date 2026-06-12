---
title: "Camera connection"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by POWMS on 2009-02-02
Hello
my wife has a compact camera (Canon A460) which when plugged into the laptop is recognised by Xubuntu and Picasa opens (which I set to open automatically when a camera is connected).
I have a new Nikon D40 and when I connect it up to the laptop, the harddrive light flickers and nothing else. Picasa does not find it and it does not even show as a removable drive on my desktop (as the Nikon does in Windows). I'm using Picasa 2.7 at the moment.
Any ideas on how to configure Xubuntu to find the Nikon?
Thanks

---

### Post by Crafty Kisses on 2009-02-02
When the camera is plugged in, run this command, and post the results back here:
```
lspci
```

---

### Post by vikramaditya on 2009-02-02
Look in the D40's menu options and see if the communication mode is switchable.  For instance, certain Canon DSLRs can be switched between "PC Connect" mode (uses the Windows WIA service) and "PTP" mode (Picture Transfer Protocol).  PTP is more widely supported and will allow you to access the memory card as a drive.

EDIT:  Just found this, from a D40 user . . .

"Setup menu - "USB "

This selects how the camera behaves when plugged into a computer via USB.

I leave it at mass storage, which means my D40 appears as an external hard drive between which I can drag and drop images and folders in my Mac OSX Finder or Windows Explorer. 

PTP is used if you want to control the D40 as an external device, for instance, via Nikon Camera Control Pro for remote camera control. PTP makes the D40 look like a device instead of like a drive. 

Use whichever works best with your computer and workflow."

---

### Post by POWMS on 2009-02-02
Thanks for the replies.
I did a google search and found this was reported as a bug (USB problem) in Linux Kernel 2.6.22 and fixed in 2.6.23.
I am currently in the middle of a large package update which includes a kernel upgrade, as I'm still on 2.6.22.
Thanks.

---

### Post by POWMS on 2009-02-02
Code
this is what I get with the camera connected:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:0b.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

---

### Post by Crafty Kisses on 2009-02-02
That's my bad I said lspci, I actually meant the following command:
```
lsusb
```
Sorry about that.

---

### Post by POWMS on 2009-02-02
Codename
I'll give that a try tonight.
I suspect that once I have finished the update I shouldn't have this problem anymore.
Thanks

---

### Post by Crafty Kisses on 2009-02-02
Hopefully not, but from that command I can see if it's even recognizing it, thanks for the update though my friend.

---

### Post by POWMS on 2009-02-03
This is what i get for lsusb:

Bus 004 Device 004: ID 04b0:0413 Nikon Corp. D40 (mass storage mode)
Bus 004 Device 003: ID 0718:0533 Imation Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

I have finished the package update and about 1 min into the package installation my desktop freezes/hangs. The hardrive light is still flashing so should I just leave it to finish installing or has the whole system crashed?
Restart in recovery mode?

---

### Post by POWMS on 2009-02-04
Well, after my system is fully uptodated, I cannot connect to my D40, though the connection is recognised as above. Any ideas on how to configure Xubuntu to launch Picasa once the D40 is plugged in?

---

