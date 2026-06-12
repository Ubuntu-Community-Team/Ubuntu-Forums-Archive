---
title: "Wireless suddenly quit working today on Compaq Presario CQ60"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by diablo75 on 2010-11-17
I have a Compaq Presario CQ60 laptop that so far as I know has never had a wireless issue in it's past.  The wireless adapter is built into the system.

This is what lspci says:

```
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

As far as I know, this wireless adapter has never required or used proprietary drivers and has always had out of the box support via the kernel modules.  However, I do have this system setup to automatically update itself with ALL updates silently (it's my wifes and she hates being annoyed by the popup for updates so I have it do it automatically, at risk of something like this happening without my knowledge of an updating taking place).

Things I have tried:

1.  Hitting the wireless adapter on/off switch to try and enable/disable the adapter at the physical level.  This does have an effect; nm-applet DOES notice the adapter being turned on and off.  If it's off, Wireless says "wireless is disabled".  But if it is ON, it says "device not ready".

2.  Checking to see if any more updates are available.  Right now I am connecting the problem laptop to the Internet via a USB teather with my cell phone, which is connected to my wireless network.  I have confirmed all updates have been applied.

3.  I have tried to access the grub menu by holding the SHIFT key down after post but it fails to see me holding the key and just continues to boot normally.  I'm not sure if there's a way to force it to display the grub menu via a configuration change (like adding a 3 second countdown by default would do the trick).  I'd like to try running with a previous kernel to see if that fixes the problem.

4.  I have not yet tried using ndiswrapper; wanted to use this as a last resort but it might turn out to be the quickest solution... I'll try this now.

In general I'm wondering if this has happened to anybody else recently, perhaps as the result of an update?  I also need a little advice about getting grub to show me a menu at boot since it's being stubborn.  Thanks!

---

### Post by diablo75 on 2010-11-17
After some testing, I've come to the conclusion that the internal wireless adapter has failed/quite/died/given up the ghost.  Fortunately they are dirt cheap (I had no idea how cheap these little things are; found one on ebay from a preferred seller in Florida giving them away for 3 bucks a piece with free shipping).

So I'll just consider this "solved" for now.

---

### Post by cpmman on 2010-11-17
What does 

```
rfkill list
```tell you?

---

### Post by diablo75 on 2010-11-18
> **cpmman said:**
> What does 

```
rfkill list
```tell you?

Absolutely nothing.  It returns no output at all.

The main way I determined this card to be defective was the fact that it wouldn't even work when booting from a Live CD; which it always had in the past.

---

