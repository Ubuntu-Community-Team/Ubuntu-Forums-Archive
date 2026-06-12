---
title: "Wireless connection not showing"
date: 2015-12-09
forum: Networking &amp; Wireless
---

### Post by tim125 on 2015-12-09
I have just installed Ubuntu 15.10 on my acer aspire 1804 laptop, everything works fine but I can not connect to the internet using the wireless card, I can connect ok when I use the cable. 
without the cable connected there is nothing to connect to ? I am a new user so forgive my limited knowledge.

The internal wireless LAN card is acer IPN2220     PCI bus 10 device 2

Hope you can help me ?

Thanks

---

### Post by chili555 on 2015-12-09
> The internal wireless LAN card is acer IPN2220 PCI bus 10 device 2Let's have a few more specifics. Please open a terminal and run and post:```
lspci -nnk | grep 0280 -A2
```Thanks.

---

### Post by tim125 on 2015-12-10
Hi thank you I have run the code lspci -nnk and have this (connected via cable)
I am sorry but I didnt know how to put the second part of he code in with the vertical line sorry....


00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 04)
	Subsystem: Acer Incorporated [ALI] Device [1025:005e]
00:01.0 PCI bridge [0604]: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port [8086:2581] (rev 04)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:005e]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:005e]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:005e]
	Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:005e]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:005e]
	Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:005e]
	Kernel driver in use: snd_intel8x0
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:005e]
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
	Subsystem: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640]
	Kernel driver in use: lpc_ich
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:005e]
	Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:005e]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV380/M24 [Mobility Radeon X600] [1002:3150]
	Subsystem: Acer Incorporated [ALI] Device [1025:005e]
	Kernel driver in use: radeon
0a:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
	Subsystem: Acer Incorporated [ALI] Device [1025:005e]
	Kernel driver in use: firewire_ohci
0a:01.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:005e]
	Kernel driver in use: tg3
0a:02.0 Ethernet controller [0200]: InProComm Inc. IPN 2220 802.11g [17fe:2220]
	Subsystem: AMBIT Microsystem Corp. T60N871 802.11g Mini PCI Wireless Adapter [1468:0305]
0a:04.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:005e]
	Kernel driver in use: yenta_cardbus
tim@tim-Aspire-1800:~$

---

### Post by chili555 on 2015-12-10
>  InProComm Inc. IPN 2220 802.11g [[COLOR="#FF0000"]17fe:2220[/COLOR]]There are no native Linux drivers for the relatively rare device. The only option is ndiswrapper. With a temporary internet connection by ethernet, tethered or whatever means possible, open a terminal and do:```
sudo apt-get update
sudo apt-get install ndisgtk
```Post #14 here has a link to the XP driver files you need. [http://ubuntuforums.org/showthread.php?t=2049417&page=2](http://ubuntuforums.org/showthread.php?t=2049417&page=2)  Download the file I've attached to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo ndisgtk
```
When the window opens, point to Desktop > Winxp > neti2220.inf. Your wireless should spring to life. Post back if you need more help.

---

### Post by tim125 on 2015-12-11
Thank you all works fine, I appreciate your help :D

---

### Post by chili555 on 2015-12-11
Glad it's working! Please use thread tools at the top to mark the thread Solved. The searchers will appreciate it.

---

