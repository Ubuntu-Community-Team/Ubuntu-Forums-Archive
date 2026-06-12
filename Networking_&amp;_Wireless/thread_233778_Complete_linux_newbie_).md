---
title: "Complete linux newbie :)"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by DeadLOK on 2006-08-10
Hi there,

I tend to consider myself very good with Windows but as I have a laptop now and use that mainly I felt like trying something different with my desktop . As unbuntu topped the overclockers favorite dist poll I decided to give that a go.

Now upon finishing the ridiculously simple installation the first thing I noticed was no network which I figured would be the case anyway as I have a wireless network.

After viewing a few other threads I've tried the following:

iwconfig which gives me "No wireless extensions" for lo, eth0, sit0.

And I looked in "Networking" and predictably its not in there either.

I then figured it was probably lack of driver so I checked device manager where I can see it in there as "Marvell W8300 802.11 Adapter" which under Windows would normally show the driver is installed.

Under the device tab it says "Device Type: Unknown" which appears to be the same for most of my devices which are working anyway. Under Advanced theres a bunch of information that I'm too lazy to write out on my laptop unless you need it.

Ok so thanks for reading that, can anyone help me or give me some advice on where to find a solution it would be mostly appreciated :)

---

### Post by stinerman on 2006-08-10
What does "lspci" output?

---

### Post by DeadLOK on 2006-08-10
deadlok@razor:~$ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (r ev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller  (rev a1)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Proces sing Unit (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
**0000:01:0a.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 80 2.11 Adapter (rev 07)**
0000:01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARai d] Serial ATA Controller (rev 02)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GT ] (rev a1)

---

### Post by stinerman on 2006-08-10
Apparently there is no native driver for your card.  You're going to be stuck with ndiswrapper.

Check [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) for a tutorial.

---

### Post by DeadLOK on 2006-08-10
Ok thanks for your help I may try and wire it and if not ill give that a shot.

---

### Post by sharperguy on 2006-08-10
You should try ndiswrapper first because if its going to work it should be pretty easy to get going.

Does anyone know which chipset the card uses as that can have a profound effect on how easy it is to get going.

---

### Post by varean on 2006-08-11
As a tip, I always found Ndiswrapper to be more compatible with drivers for Wifi cards/adapters that came on the CDs that shipped with your computer. If you laptop came with any CDs, look for the drivers for your wifi adapter and try to use those with ndiswrapper.

---

