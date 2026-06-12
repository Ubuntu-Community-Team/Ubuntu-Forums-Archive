---
title: "hardware minimums for Ubuntu Studio?"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by pnodiff on 2010-10-01
Looking for hardware minimums from users of Ubuntu Studio. ie: CPU speed/brand, motherboard, ram, video card, etc to install Ubuntu Studio without Windows on a PC. If a user has built their own PC and Ubuntu Studio audio/video/graphic apps run great, please share what hardware you used. Pete

---

### Post by hhh on 2010-10-01
Ubuntu Studio has the same system requirements as Ubuntu (256 MB of memory), though some of the multimedia apps it installs probably need more memory. Like Ubuntu. you can run it live by burning the ISO to a cd or transferring it to a 1G or greater USB drive via Unetbootin. Fire it up and play around to see if it's worth installing it on your system.

HTH

---

### Post by davidmohammed on 2010-10-01
... the minimum [ubuntu specs]("https://help.ubuntu.com/community/Installation/SystemRequirements") are not 256MB - more like 1GB


you'll only get ubuntu to run on 256 by doing a custom install using something like ubuntu minimal or something like lubuntu.

Studio will run ok on the recommended ubuntu spec.  More RAM and CPU will help with audio editing etc.

---

### Post by pnodiff on 2010-10-01
My son is an amazing artist and a Ubuntu user friend burned me an install DVD of Ubuntu Studio for my son to try. But our home PC's are under 2Ghz AMD with 512M ram and only integrated graphics. I looked through Craigslist for a decent used PC but at prices asked, I might as well build one or even by a 'bare bones' pre-built from New Egg or Tiger Direct etc. Any specific suggestions about CPU speed/type as in Dual Core Intel or AMD and motherboard... Pete

---

### Post by hhh on 2010-10-01
> **davidmohammed said:**
> ... the minimum [ubuntu specs]("https://help.ubuntu.com/community/Installation/SystemRequirements") are not 256MB - more like 1GB
Thanks. I don't know why the Wiki release notes say otherwise...
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

---

### Post by Legendary_Bibo on 2010-10-01
> **pnodiff said:**
> My son is an amazing artist and a Ubuntu user friend burned me an install DVD of Ubuntu Studio for my son to try. But our home PC's are under 2Ghz AMD with 512M ram and only integrated graphics. I looked through Craigslist for a decent used PC but at prices asked, I might as well build one or even by a 'bare bones' pre-built from New Egg or Tiger Direct etc. Any specific suggestions about CPU speed/type as in Dual Core Intel or AMD and motherboard... Pete

If your son is working with graphics you'll need a decent graphics card and processor. Intel dual cores are more pricey, but they're better than AMD. Also Nvidia works great with Ubuntu. Audio stuff will require a good processor mainly, and I would stick with Intel. Having a low amount of RAM will bottleneck the processor, so I would get probably 4gb with a 64-bit dual core.

---

### Post by JC Cheloven on 2010-10-01
> **pnodiff said:**
> Looking for hardware minimums from users of Ubuntu Studio. ie: CPU speed/brand, motherboard, ram, video card, etc to install Ubuntu Studio without Windows on a PC. If a user has built their own PC and Ubuntu Studio audio/video/graphic apps run great, please share what hardware you used. Pete
Full time UbuntuStudio user here. I stick with karmic 9.10, which I'd recommend at the moment. Working like a charm.

First of all, please note that the hw minimum for installing can be pretty  undemanding. Despite official recommendations, 512 MbRAM will suffice, specially if you have set some swap space in your disc. A single core processor at, say, 1GHz, will move your desktop and audio apps quite smoothly. An integrated graphics chipset will do as well...  
Don't get me wrong: the above is meant for simply installing and trying out Ubuntu(-Studio) and its apps. But, although you can work marvels with such a modest computer, to use audio&video apps in a comfortable professional-like manner, you'll need a little more ( > 1GbRAM and a decent graphics card are the most important imo).

That said, here my specs (you asked for):

Motherboard ... Asus P5W DH deluxe
Processor ... 4-core intel Q6700  2.66GHz 
Graphics ... Nvidia Gforce 7300 GT
RAM ... 4Gb DDR2
audio ... pci Hammerfall DSP 9632 (requires tweaking to work!)
(& several external audio devices, both firewire and usb, & and an integrated intel audio chipset)

---

