---
title: "Wireless Connection problem with Ubuntu 14.04 for Toshiba Qosmio Intel I7"
date: 2015-05-22
forum: Networking &amp; Wireless
---

### Post by m-veron622 on 2015-05-22
Hello,

I've tried to post about this before in the past, but was unable to receive any help. My problem is that I am unable to connect to a wireless network point except my home. Anytime I try to go somewhere and connect to the internet the Network Monitor that is stock with Ubuntu 14.04 says that the NW Interface is down. Strangely enough though I believe the network adapter is working because when I launched an SSID finding program it is able to show me some network traffic. Please help! (I am typing off of a different laptop so I will provide code from my terminal in the response)

---

### Post by kc1di on 2015-05-22
Hello,
you may want to give wifi radar a try it's in the repository. It's very good at finding wireless networks.
My other thought is do you have any kind of firewall enabled that is blocking networks other than your own?
also could you supply the outputs of the following terminal commands.

```
lspci
```
and 
```
rfkill list all 
```

---

### Post by m-veron622 on 2015-06-07
I apologize about the delay! And no firewall installed at the moment. 


00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF114M [GeForce GTX 670M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF114 HDMI Audio Controller (rev a1)
07:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
08:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

