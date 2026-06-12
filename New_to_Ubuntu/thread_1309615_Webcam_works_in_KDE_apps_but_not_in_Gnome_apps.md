---
title: "Webcam works in KDE apps but not in Gnome apps"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Kapitän Rotbart on 2009-11-01
I just got an Asus T91. It's a very cool machine, and so far I've been running Karmic in a live session on it (I'm going to install Karmic soon, I haven't actually used the windows xp oem yet and I don't plan on using it, either.

The built-in webcam is nothing special, it's 0.3 MP but it does generate a nice enough image for chatting and such. I've only tried the (Gnome) Ubuntu Netbook Remix on this machine so far, but I doubt using a different desktop environment would change hardware compatibility (plus I am a Gnome fan...I much prefer the layout of the Gnome Netbook Remix than the KDE Netbook Remix. Mind you the KDE Netbook Remix would likely make more sense for a touch screen netbook, but I'm not going to be the first to use the KNR).

I tried the webcam in a few apps (it's /dev/video0). Cheese and Emesene (both Gnome) will not recognize it. Kamoso and apparently Skype (both KDE) support it perfectly. I really don't understand how if the webcam works in Linux with the bundled drivers in KDE apps, why it wouldn't work in Gnome apps! aMSN supports it as a "Video 4 Linux 2 USB Camera" (which is neither Gnome nor KDE).

Here is the output for lspci and lsusb:
> ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)


ubuntu@ubuntu:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 13d3:509b IMC Networks 
Bus 001 Device 004: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 003: ID 0471:0831 Philips 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0b05:b703 ASUSTek Computer, Inc. 
Bus 004 Device 002: ID 1cb6:6680  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I still haven't found the webcam in that output, so I don't know if I need a special driver. Is there a way to get Gnome to detect it?

---

### Post by Kapitän Rotbart on 2009-11-02
Bump.

---

