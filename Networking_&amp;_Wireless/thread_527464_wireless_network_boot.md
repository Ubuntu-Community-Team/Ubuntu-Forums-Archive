---
title: "wireless network boot"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by justDIY on 2007-08-16
I have several pentium class notebooks that are more or less junk - they are too slow to do anything productive with, on an interactive level at least.

What I was thinking about is having them be networked picture frames, booting wirelessly off the network to save some power (no hard drive to spin) and mostly to save noise (no old hard drives whirring!)

Since wireless cards don't normally have a pxe component, I was planning on using small inexpensive compact flash drives to load pxelinux into the computers ram, and then the bootloader can load the modules for wireless, contact the bootp server and do its thing.  sure it might be a bit slow over the wifi, but I don't really care!

so my goals are:

1) get pxelinux onto a compact flash card, so that the computer loads it into memory
2) figure out how to make pxelinux configure the wireless card to connect to my AP (no encryption or password for now)
3) setup a nfsroot on my server to publish a stripped down ubuntu
4) setup an image gallery program, maybe an rss reader or weather script too?

Does anyone have any tips regarding steps one and two?  

Looking at pxe's cousin, syslinux, I'm going to try copying pxelinux straight to sector 0 of the cf card, which is where syslinux would live.  perhaps the bios will then read it in and proceed to execute the bootloader.

For step 2, I'm at a loss right now, I need to do more research.

What do you think gang?

---

### Post by ihristov on 2007-08-17
Just an idea. Use wired instead of wireless. This way you will not need flash cards.

Since apparently you don't have wired network where you want to connect it use a wireless bridge.

I have used with lots of success Motorola WRT54 hardware version 2. $30 - $40 on eBay (they are equivalent to Linksys WRT). I use the dd-wrt firmware to put the access point in "client bridge" mode. If can be done in "transparent client bridge" or with natting in a separate network.

---

### Post by justDIY on 2007-08-17
> **ihristov said:**
> Just an idea. Use wired instead of wireless. This way you will not need flash cards.

that would work on a modern computer.

The books I'm using are too old, or perhaps just too cheap, to support network booting.  Their only options are hard drive, floppy and cdrom.

---

### Post by ihristov on 2007-08-19
Network booting AFAIK depends mostly on the network adapter. If you have a network adapter that supports network booting you should be good.
[http://www.etherboot.org/db/](http://www.etherboot.org/db/)

But, if you are using Flash cards you should be able to do what you want - i.e. load the wireless drivers and load the OS from the central server.

I was just suggesting a configuration that would be easier/cheaper, assuming your network adapter can boot and specially if you have several clients close to each other.

---

