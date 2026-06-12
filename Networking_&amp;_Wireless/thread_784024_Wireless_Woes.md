---
title: "Wireless Woes"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by Richpickings on 2008-05-06
Hi Chaps
I am very new to Linux and Ubuntu. I have an Asus X50RL laptop dual boting Ubuntu 8.04 and XP Pro. I cannot seem to get the wireless networking to work at all. I believe from reading other posts that the following information may be useful:

ruan@ruan-laptop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01) 
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA 
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) 
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) 
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) 
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) 
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) 
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13) 
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia 
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] 
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) 
06:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0) 
ruan@ruan-laptop:~$ 

Thanks for your help.

---

### Post by Richpickings on 2008-05-06
I'm assuming it's the line that says: 00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01) that is the problem.

---

### Post by ivze on 2008-05-06
You seem to be in trouble, becouse if something don't work out-of-the-box that's rather diffcult to overcome.
You may: 
1. Wait half a year for Ubuntu - Interpid Ibex .
2. Try to solve your problems manually. However, that's a difficult way.
If you agree with (2), these links are for you:
  Try this - installing a newer version of madwifi drivers:
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)
  See ndiswrapper Ubuntu package. Ndiswrapper helps make a linux wifi driver of a Windows one. If you have good luck, this will help you.
Have much good luck!

---

