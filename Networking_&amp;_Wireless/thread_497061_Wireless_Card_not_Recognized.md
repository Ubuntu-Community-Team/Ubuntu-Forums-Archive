---
title: "Wireless Card not Recognized"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by LJarvis on 2007-07-09
Ok im trying to install my linksys WMP54GS pci card on Ubuntu with ndiswrapper but my card is not detected in Ubuntu. I found an unknown pci device in device manager which I assume is my card. How can I get Ubuntu to recognize my card? When I run windows xp on the same computer the card is recognized and works fine.

---

### Post by kevdog on 2007-07-09
With the card plugged in please post:

lspci -nn
lshw -C network

Might be a driver issue.

---

### Post by LJarvis on 2007-07-09
This is what i got for lspci -nn
> 00:00.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:036a] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2)
00:04.0 IDE interface [0101]: nVidia Corporation MCP55 IDE [10de:036e] (rev a1)
00:05.0 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:05.1 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:05.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:06.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI bridge [10de:0370] (rev a2)
00:06.1 Audio device [0403]: nVidia Corporation MCP55 High Definition Audio [10de:0371] (rev a2)
00:08.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2)
00:09.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2)
00:0a.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0376] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0374] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0374] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0378] (rev a2)
00:0e.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0375] (rev a2)
00:0f.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0377] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:08.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
01:0b.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
06:00.0 SATA controller [0106]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 03)
06:00.1 IDE interface [0101]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 03)
07:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:0421] (rev a1)


lshw -C network

> WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth2
       version: 03
       serial: 00:0f:66:1c:d6:c6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=32 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:fdefc000-fdefdfff irq:22


---

### Post by kevdog on 2007-07-09
Your card is recognized:

01:08.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

Its just that something is wrong with the driver.  Did you try to install any type of driver - bcm43xx or ndiswrapper??

---

### Post by LJarvis on 2007-07-09
I installed ndiswrapper with the same driver I used to install the card when my box is running windows.

Im using ubuntu's guide for installing ndiswrapper ([https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless)) its says to use the command > ndiswrapper -l to see if the installation worked. When I used this command I got this:
> drivername : invalid driver!
wmp54gs : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
wmp54gsa : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)


---

### Post by LJarvis on 2007-07-09
I just checked the bcm43xx site that you mentioned and my card is supported by the driver. The site said something about the driver being included in ubuntu so how can I install that?

---

### Post by kevdog on 2007-07-09
Looks like you are half way home with ndiswrapper so lets stick with this plan first.  Our fall back is bcm43xx.  Always good to have two potential plan of attacks:)

Before installing new drivers with ndiswrapper, you always have to remove to old one or successive attempts will always fail.

So the bruce force way of doing this is:
cd /etc/ndiswrapper
sudo rm -R *

Then check the directory
ls
There should be no files or directories listed.  If there is anything in the directory, delete it.

Then try reinstalling the driver!

---

### Post by LJarvis on 2007-07-09
It Worked! Thanks so much Kev for all the help :)

---

### Post by kevdog on 2007-07-09
So you have an internet connection????  Great job.  Hope you learned something!

---

