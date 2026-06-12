---
title: "Belkin F5D7010 v7 in Compaq Armada 110"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by Chris_Ba on 2008-02-11
As is stated in the title I am trying to get a Belkin F5D7010 card working in an Armada 110 running Xubuntu 7.10. I have referred to this thread " [http://ubuntuforums.org/showthread.php?t=187004&highlight=f5d7010](http://ubuntuforums.org/showthread.php?t=187004&highlight=f5d7010) " trying to get it to work, all steps went smoothly but the last. It seems when I type sudo gedit /etc/modules, nothing happens. Sometimes it asks me for my password but even then it just brings me back to terminal. Would not being able to modify that file prevent the card from registery entirely? I run Xubuntu on my desktop too, and the same thing happens when I try to run that command. It just sits. When I plug the card into the computer nothing happens, no lights turn on, no sound, no screens. I'm trying to put together a budget laptop for college, any help in getting this sucker working is appreciated.

---

### Post by Chris_Ba on 2008-02-11
Alright, I got the sudo gedit command working. Aparently Xubuntu doesn't come with that pre-installed? Anyways, I got the driver loaded and the wireless windows driver application working. But, as you can see in the screenshot, the hardware is not detected. How can I check to see that my computer is recognizing its pcmcia port? As I said, there are no lights coming on on the card. Even after I was able to modify the /etc/modules file.
Thanks, Chris

---

### Post by Chris_Ba on 2008-02-12
Alright, I know somebody on here has got to know how to fix this. Searching around I've come across a few things I can do to figure out whats happening.
Running lshw in terminal yields a pretty good list, ones I believe may be of some importance:

*-bridge UNCLAIMED
 description: Bridge
 product: VT82c686 [Apollo Super ACPI]
 vendor: VIA Technologies, Inc.
 physical id: 7.4
 bus info: pci@0000:00:07.4
 version: 30
 width: 32 bits
 clock: 33MHz
 capabilities: bridge cap_list
 configuration: latency=0

*-pcmcia
description: CardBus bridge
product: PCI1410 PC card Cardbus Controller
vendor: Texas Instruments
physical id: a
bus info: pci@0000:00:0a.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pcmcia bus_master cap_list
configuration: driver=yenta_cardbus latency=176 maxlatency=5 module=yenta_socket

*-network UNCLAIMED
description: Ethernet controller
product: Belkin
vendor: Belkin
physical id: 0
bus info: pci@0000:02:00.0
version: 20
width: 32 bits
clock: 33MHz
capabilites: cap_list
Configuration: latency=0 maxlatency=64 mingnt=32

Given that I have no idea what I'm looking for, I'm not sure, but the UNCLAIMED bit seems like it isn't quite right.

The integrated ethernet adapter which functions properly goes as follows.

*-network
description: Ethernet interface
product: 82557/8/9 Ethernet Pro 100
vendor: Intel Corporation
physical id: 9
bus info: psi@0000:00:09.0
logical name: eth0
version: 09
serial: 00:d0:59:80:81:60
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes

Any help is appreciated.

---

### Post by Chris_Ba on 2008-02-12
Well, I got it working, thanks for all your help guys. I ended up doing what it says here [http://ubuntuforums.org/showthread.php?t=489368&highlight=install+driver+using+ndiswrapper](http://ubuntuforums.org/showthread.php?t=489368&highlight=install+driver+using+ndiswrapper) and it worked great!

---

