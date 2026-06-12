---
title: "Airlink+ AWLL3025"
date: 2005-05-20
forum: Networking &amp; Wireless
---

### Post by malachakla on 2005-05-20
Hello, I just installed Ubuntu on my formerly Windows XP PC.
To get onto the Internet, I have been using an Airlink+ AWLL3025 USB 2.0 802.11g adapter.
Ubuntu does not automatically recognise my adapter, and I have absolutely no clue of how to get it working.
Can anyone help?
Thanks a lot!

---

### Post by Magneto on 2005-05-24
if you still havent gotten it working yet try this

[http://www.qbik.ch/usb/devices/showdev.php?id=3084](http://www.qbik.ch/usb/devices/showdev.php?id=3084)

look at the comments - the bottom most remark may be the easiest course. Im about to buy 2 of those.

---

### Post by malachakla on 2005-05-24
Danke schoen, I'll try it.
I had looked at these drivers, but I didn't know exactly which Zydas chipset the adapter uses.

---

### Post by malachakla on 2005-05-24
Okay, I compiled the module and installed, now how do I run the module?
It's always the little things that hang me up  :) 
Thanks.

---

### Post by Magneto on 2005-05-27
modprobe zd1211

---

### Post by malachakla on 2005-05-27
Thanks :)

---

### Post by Eppenetus on 2005-05-27
I also am having problems with finding the network and accessing it from a AirLink10 AWLH3025 PCI card.  The local Fry's (Burbank Cal) put them on sale for $9.99 US and I bought one thinking it could be installed using NDISWRAPPER.  No Joy Here. it did'nt work but I keep trying.  The card works OK with <ugh> WIN XP but no work with Linux.  Any ideas out there?

---

### Post by brousch on 2005-08-02
I put up a wiki with ubuntu-specific instructions for the zd1211.
[https://wiki.ubuntu.com/zd1211wifi](https://wiki.ubuntu.com/zd1211wifi)

---

