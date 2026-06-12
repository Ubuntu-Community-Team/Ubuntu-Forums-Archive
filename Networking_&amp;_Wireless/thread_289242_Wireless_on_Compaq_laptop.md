---
title: "Wireless on Compaq laptop"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by AudioMove on 2006-10-30
Hi, just installed kubuntu on my compaq presario laptop , however when i try to enable the wireless device (eth1) in the network settings in the control centre it enables for a second but disables again. I've set wireless up on my kbuntu desktop before but never had this issue, Can anyone explain why this is happening?

---

### Post by dmizer on 2006-10-30
it'll help to know what wireless chipset you're using.  is it an internal device or a pcmcia card?

post the output of lspci

---

### Post by -Chi.0 on 2006-10-31
Check this link for help w/ NdisWrapper on Edgy](*,) 
[http://ubuntuforums.org/showthread.php?p=1692550#post1692550]("http://ubuntuforums.org/showthread.php?p=1692550#post1692550")
I hope this helps:-k

---

### Post by AudioMove on 2006-10-31
HI dmizer,

lspci output:

0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:04.0 PCI bridge: ATI Technologies Inc: Unknown device 5a36
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 01)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
0000:03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:03:04.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
0000:03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

It is an internal wireless device. From the output seems to be a broadcom wireless device.

And i have installed ndiswrapper-utils

---

### Post by dmizer on 2006-11-08
sorry ... i've been tied up.  if you're still having trouble, check this thread.  looks like you'll need ndiswrapper.

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

---

