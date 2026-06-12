---
title: "WMP54G wireless card does not appear- driver problem?"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by banditthecooldog on 2010-05-15
Ok, I've done alot of research on getting this linksys WMP54G card to work in linux, but I haven't found a way to do it in my particular distro and I'm kind of lost for the first time in a year and a half using Ubuntu! Any help would be GREATLY appreciated :)
 
I was running regular (as in not Studio) Ubuntu ver 8.04, 8.10, 9.04, 9.10, and briefly 10.04 (all 32-bit) and the card appeared as soon as the system was installed with no issues. Ubuntu seems to have a native driver for this card. I recently installed Ubuntu Studio 10.04 64-bit and now the card does not appear. I'm not sure if the problem is Ubuntu Studio, or if it's the 64-bit?
 
I searched using ndiswrapper and found this page:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
but under section 2.2.1 "Currently supported releases", 10.04 is not on there and I'm not sure exactly how to use ndiswrapper anyways...
 
I have no access to the internet through linux, I am currently running an XP dual boot and I can use the linksys card through Windows to get to the inernet.
 
 
 
command 'lspci' retuns this:
 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI

---

### Post by WinterRain on 2010-05-15
> **banditthecooldog said:**
> 
04:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI

This is your wireless card, as the wmp54g uses the ralink chipset. I use the same exact model with no issues. When you left click the network icon on the panel, what happens?

---

### Post by banditthecooldog on 2010-05-16
The network icon does not appear in the panel. When I go to the system > administration > network, it also does not appear? It's almost as if the computer doesn't know the hardware exisits.
 
Thank you for you reply by the way

Update: I got fed up with windows (not hard to do) and replaced it with Ubuntu 10.04 32-bit. The card works here, but still does not work in the Ubuntu Studio side of the computer.

---

### Post by banditthecooldog on 2010-05-20
Fixed it! It's fairly unscientific and I'm sure all the people who actually know what they're doing will laugh at me, but I don't care cause I got it to work-

Heres what I did:

Put in my installation CD
Went to: pool/main/n/
Installed EVERY file in EVERY folder that started with "Network_Manager_something something blah blah blah..." You get the Idea...
Restarted the computer

Then the network icon showed up on the panel and I was able to connect right away. Because Linux has a native driver for my wireless card I didn't have to go out finding one, my issue was actually not having the network manager installed in the first place.

---

