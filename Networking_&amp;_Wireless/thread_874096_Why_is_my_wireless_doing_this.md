---
title: "Why is my wireless doing this?"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by Brainal on 2008-07-29
Alright. I currently have a Linksys WMP300N and got it to work via anewguy's method on Hardy Heron (64-bit). I tried 32-bit and the problem still persists. The problem is is that I ALWAYS get disconnected and is starting to make me really irate. It happens when I'm downloading stuff. It just disconnects...sort of. Network Manager says it's connected but Firefox says otherwise. I am forced to either restart my computer or reinstall my wireless driver. It's making me so mad, that I'm starting to think that Vista is BETTER.

Oh, and if you wanted this:
```
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
02:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
04:07.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
04:08.0 Multimedia audio controller: Creative Labs SB Audigy LS
04:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
```
```
  *-network               
       description: Wireless interface
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: wlan0
       version: 01
       serial: 00:1c:10:e7:04:94
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Linksys, A Division of Cisc ip=192.168.0.186 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

---

### Post by kdorf on 2008-07-29
I had a similar problem with my Realtek wireless and it was a driver problem. I note that you are using ndiswrapper. Try updating your Windows driver to the latest version. You might also see if there is a native Linux driver yet available.

---

### Post by Brainal on 2008-07-29
> **kdorf said:**
> I had a similar problem with my Realtek wireless and it was a driver problem. I note that you are using ndiswrapper. Try updating your Windows driver to the latest version. You might also see if there is a native Linux driver yet available.
The funny thing is is that on my Vista partition, there's a folder with the Vista drivers and XP drivers. I copied the XP drivers to my Ubuntu partition and tried to use that. The "Windows Wireless Drivers" thing says that they're invalid. The ones I'm using somehow work for some reason. :-k

---

### Post by Brainal on 2008-07-30
Another thing I found out is that the card is only using the G signal instead of N. I'm not all that picky, but it would be nice to be the N signal. I'm starting to just give up and completely remove Ubuntu for Vista which I'm starting to think is much better.

---

### Post by cdtech on 2008-07-30
I have the same "ndis and driver", have you tried using "wicd" (sudo apt-get install wicd). I've found this program to be much better than the Network Manager.

Hope this helps........

---

### Post by Brainal on 2008-08-01
> **cdtech said:**
> I have the same "ndis and driver", have you tried using "wicd" (sudo apt-get install wicd). I've found this program to be much better than the Network Manager.

Hope this helps........

I have. I just can't figure out how to connect. I enter my WPA key and it doesn't connect for some reason. I just reformated my computer. I'll try it again and see if it works


Edit: I installed wicd and it seems to be working fine. I haven't had any drop outs at all. Hopefully it'll stay like this

---

### Post by Bizz on 2008-11-05
I REALLY hate to bump this, but it was so relevant to my problem...

I'm having the same difficulty as the OP, but unfortunately wicd doesn't exist anymore (?).

Help? :)

EDIT: Disregard this, I'm a fool.

---

