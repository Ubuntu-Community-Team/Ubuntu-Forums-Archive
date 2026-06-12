---
title: "The Wireles problem again.... for newbie"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by dsttnole on 2008-12-26
basically cant connect to the internet with wireless

I read lots of the post and try different stuff, im learning so so far, here is what i can give you:

ok here is the terminal for lspci,  i have download3ed wifiradar but that didnt work... it wont even start

[COLOR="DarkOrange"]00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
[/COLOR]


now what?!!! :S

---

### Post by gettinoriginal on 2008-12-27
Don't know if you have tried this one, hope it helps:  :P

[http://ubuntuforums.org/showthread.php?t=975948](http://ubuntuforums.org/showthread.php?t=975948)

---

### Post by RomeReactor on 2008-12-27
Hi. Try this:
```
lspci -nn | grep Ethernet
```
If the result for the Marvell device contains **11ab:2a08**, maybe [this thread]("http://ubuntuforums.org/showthread.php?t=575785") can be of help.

---

