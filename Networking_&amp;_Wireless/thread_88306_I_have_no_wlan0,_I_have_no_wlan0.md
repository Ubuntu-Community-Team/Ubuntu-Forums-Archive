---
title: "I have no wlan0, I have no wlan0"
date: 2005-11-09
forum: Networking &amp; Wireless
---

### Post by K2712 on 2005-11-09
My driver is installed, breezy sees my card, the light on my card is on, yet despite my best efforts I cannot bring up my wlan0 connection.  I put this in a previous post:

Here is my lspci output:

0000:00:00.0 Host bridge: Intel Corp. 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82815 815 Chipset AGP Bridge (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BAM ISA Bridge (LPC) (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801BAM IDE U100 (rev 03)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
0000:02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
0000:02:06.0 PCI bridge: Actiontec Electronics Inc Mini-PCI bridge (rev 11)
0000:02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
0000:02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
0000:02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
0000:08:04.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 0
0000:08:08.0 Communication controller: Lucent Microelectronics WinModem 56k (rev 01)
0000:09:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

"sudo iwlist wlan0 scan" gives me this:
wlan0 Interface doesn't support scanning

"sudo ifup wlan0" gives me this:
Ignoring unknown interface wlan0=wlan0.

"iwconfig" gives me this:
lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.


Can anyone help me please??

---

### Post by Verbious on 2005-12-19
did you add the device to /etc/network/interfaces?

sudo gedit /etc/network/interfaces

iface wlan0 inet dhcp

auto wlan0

---

