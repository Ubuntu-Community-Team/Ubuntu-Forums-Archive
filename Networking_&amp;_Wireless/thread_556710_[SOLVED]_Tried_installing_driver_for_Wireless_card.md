---
title: "[SOLVED] Tried installing driver for Wireless card &amp;amp; now it won't recognize it..."
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by messybricks on 2007-09-21
So...

I tried installing the driver for my Wireless Adapter (D-Link AirPlus Xtreme G DWL-G650 Revision B4, pci id: 168c:0013), using ndiswrapper.  I used the driver recommended on ndiswrapper's website, and followed the instructions to get it installed.

When I went to find out whether or not the installation was "valid", it told me that the driver was installed, but the device was not present.  It was then that I noticed that the green light wasn't flashing anymore.

What's worse is that my onboard NIC (which was working fine before) is no longer working, nor is it even recognized.  

I'm using the newest version of Ubuntu (installed two days ago with all the newest updates).


Update: 9/22: I can't get it to mount anything on the USB ports... (USB drives, USB hard drive, etc).  These at least are recognized by the terminal, but they don't seem to want to mount.

---

### Post by messybricks on 2007-09-22
I figured out that the problem was with the new kernel I updated to (the one with a 16 in it)... I went back to a previous kernel (with a 15 in it), and it all works fine- USB, Wireless, NIC, etc.

---

