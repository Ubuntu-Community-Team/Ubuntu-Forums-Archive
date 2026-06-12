---
title: "No internet; ethernet and wireless don't work"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by hydra198 on 2008-09-22
I've got an HP Pavilion tx2000 that I'm putting Ubuntu on.  I'm aware of the problems HP's have with wireless.  But as far as I know I should be able to get wired internet 'out of the box' right?

I can get by for now without the wireless working (I should be able to get it working from the numerous other threads on here).  But it would really help if I actually had internet access...

Here are the results from lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

---

### Post by M42 on 2008-09-22
Yes, it has been a while since I first put Ubuntu on my tx2000 but I'm quite sure that wired internet should work "out of the box".  I don't know much about networking but you might try a couple of thing.  
First, has your wired internet worked in Vista?
Does the port on your tx2000 show a green light on the left side when facing the tx2000 internet socket?
If data is flowing you should also see a yellow light on the right side of the socket when connected.
Have you tried swithching to a different port on your router?
Have you tried switching internet cables?
Based on your output Ubuntu appears to be finding your Broadcom card.
If none of these work you might try getting the wireless working.  It is fairly straigh forward and at least you would have internet connectivity.
That is about the extent of what I can suggest.
Good luck!

---

### Post by superprash2003 on 2008-09-22
read this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by hydra198 on 2008-09-22
> **M42 said:**
> Yes, it has been a while since I first put Ubuntu on my tx2000 but I'm quite sure that wired internet should work "out of the box".  I don't know much about networking but you might try a couple of thing.  
First, has your wired internet worked in Vista?
Does the port on your tx2000 show a green light on the left side when facing the tx2000 internet socket?
If data is flowing you should also see a yellow light on the right side of the socket when connected.
Have you tried swithching to a different port on your router?
Have you tried switching internet cables?
Based on your output Ubuntu appears to be finding your Broadcom card.
If none of these work you might try getting the wireless working.  It is fairly straigh forward and at least you would have internet connectivity.
That is about the extent of what I can suggest.
Good luck!

No lights on the port when connected, it does work in Vista.  Tried all the router ports with 2 different cables.

> **superprash2003 said:**
> read this [http://prash-babu.blogspot.com/2008/...-in-linux.html](http://prash-babu.blogspot.com/2008/...-in-linux.html)

No luck, thanks for trying though.

Any other ideas?

---

### Post by M42 on 2008-09-22
I'm beyound my depth at this point but it may be that somehow netowrking is being turned off during bootup.  Try this command in a terminal window:

sudo /etc/init.d/networking restart

I'm running Kbuntu at this time so I'm not as familar with Ubuntu utilities.  I belive Ubuntu has a networking utility which you might bring up and see if the wired networking appears to be running.  

If this doesn't work the only other thought I had was to do a fresh install of Ubuntu.

---

### Post by Iowan on 2008-09-22
The 4310 doesn't appear in [this]("http://ubuntuforums.org/showthread.php?t=880218") thread (at least not in the first post).  More basic system informatin might help... results of **ifconfig** and contents of **/etc/network/interfaces**.

---

### Post by hydra198 on 2008-09-23
Got wireless working yesterday with [this]("http://www.colinblog.com/2008/04/how-to-install-broadcom-bcm4310-usb.html") guide.  Haven't tried wired since.

Anyways, thanks for the help.

---

