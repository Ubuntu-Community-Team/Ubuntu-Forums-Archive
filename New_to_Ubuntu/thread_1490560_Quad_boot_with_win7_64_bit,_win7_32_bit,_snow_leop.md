---
title: "Quad boot with win7 64 bit, win7 32 bit, snow leopard and ubuntu"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by shilongblues on 2010-05-22
Dear Gurus,
I just finished building a PC with following configuration:
Motherboard : Gigabyte X58A-UD 3R
Processor:  Intel i7 930
Video card: XFX ATI RAEDON 5770
Hard drive: 2 X Samsung sinpoint 1TB 
RAM: 6x 2 GB G.Skill DDR3-1600 PC3-12800
PSU: Corsair HX-650W
Monitor: Dell ST2410

I want to have a quad boot in hard drive 1 with following operating systems:
Win 7 32 bit Pro, Win 7 64 bit Pro, Snow Leopard and Ubuntu 10.04. 
I want keep hard drive 2 for data which should be accessible from all OSs.

I would highly appreciate if anyone can help me in this project.

---

### Post by dfreer on 2010-05-22
You will need a modified BIOS just to run Snow Leopard IIRC. I couldn't even begin to describe how to do so, but there's plenty of guides on the internet.

Installing both 32-bit and 64-bit copies of win7 doesn't make any sense, just go 64-bit. 

The final rule of thumb is that Ubuntu gets installed last so it gets to install it's bootloader in the MBR to load all the OS's.

---

### Post by shilongblues on 2010-05-22
Thanks dfreer,
I frequently use a scientific software which does not run on 64 bit. That is why I wanted to keep win7 32 bit.
I was wondering if you can post a link to a  good guide. I am yet to find a detailed one.

---

### Post by dfreer on 2010-05-22
Well, for starters I know the it can be done, here's a video of a guy doing the same thing for his xbox mod (you can see him installing the OS at the end of the video): [http://www.youtube.com/watch?v=TggHtINGIyc](http://www.youtube.com/watch?v=TggHtINGIyc)

He uses EFIX USB chip to allow booting to OSX, although there is other ways to do so without spending the money on the chip. Here's a review of the chip with some install instructions: [http://gizmodo.com/5049756/review-efix-dongle-perfectly-transforms-pc-to-mac](http://gizmodo.com/5049756/review-efix-dongle-perfectly-transforms-pc-to-mac)

byuu, programmer of the incredible bsnes SNES emulator, posted an article about how he got OSX installed on a PC using a hacked kernel: [http://byuu.org/articles/osx86/](http://byuu.org/articles/osx86/) He runs his own forums so you might be able to get specific questions answered by him.

A guide that looks really indepth with no hacking required: [http://lifehacker.com/5360150/install-snow-leopard-on-your-hackintosh-pc-no-hacking-required](http://lifehacker.com/5360150/install-snow-leopard-on-your-hackintosh-pc-no-hacking-required)

---

### Post by oldfred on 2010-05-22
If you want to directly boot each windows from grub you have to separately install them. Windows will combine boots into the first install on a primary partition. The second install then only boots thru the first. Install both windows to primary partitions.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by srs5694 on 2010-05-22
The moderators frown on discussions of running OS X on non-Apple hardware, since doing so violates Apple's EULA. Therefore I won't say much about that topic.

One issue you may encounter is the number of primary partitions required. Linux is happy to install entirely on logical partitions, but not so your other choices. Therefore, you'll have to be careful not to let either Windows installation grab two primary partitions. There may be ways to let both Windows installations share a single primary, with the bulk of each installation going on a logical partition, but I'm far from an expert on that. It's worth looking into further, though. Another option is to use a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which is ugly and dangerous but useful for letting certain OS combinations coexist. When presented with a hybrid MBR, Windows sees the MBR partitions (up to three primary partitions) but most other modern OSes (such as Linux and OS X) see GPT partitions.

Another option is to split your OS installations across the two disks. This is actually beneficial in several ways, since it takes some of the pressure off in terms of the number of primary partitions. You could also use MBR on one and GPT on the other, should that prove to be convenient.

---

### Post by cariboo on 2010-05-29
As srs5694 said we don't support software piracy on the forums. You will have to go elsewhere to solve your OSX problem. Thread closed.

---

