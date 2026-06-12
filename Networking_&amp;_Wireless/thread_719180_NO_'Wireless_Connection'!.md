---
title: "NO 'Wireless Connection'!"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by Truffs on 2008-03-08
I have intalled ubuntu 7.10 Gutsy on my laptop and i get no 'wireless connection' option in system>administration>network when trying to configure and open the network.
I've been searching but i just can't seem to solve the problem on my own. 

Here are some outputs of some commands that may be useful. Thanks in advance!

Result to **sudo lshw -C network**:
*-network
description: Ethernet interface
product: NetLink BCM5787M Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 02
serial: 00:1d:72:0e:ce:f8
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair
*-network UNCLAIMED
description: Ethernet controller
product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
vendor: Atheros Communications, Inc.
physical id: 0
bus info: pci@0000:04:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix cap_list
configuration: latency=0

Result to **lspci**:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
0f:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0f:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0f:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

Result to **iwconfig**:
lo no wireless extensions.

eth0 no wireless extensions.

irda0 no wireless extensions.

Result to **sudo iwlist scan**:
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

irda0 Interface doesn't support scanning.

Result to** cat /etc/network/interfaces**:
auto lo
iface lo inet loopback

---

### Post by alphacrux on 2008-03-26
looks like a driver problem to me. There ought to be a bunch of posts about this on the ubuntu forums, ill try to find you some when I have some spare time. You will probably have to:
A) blacklist a competing driver in /etc/modprobe.d/blacklist
B) download a new driver from aptitude, or better yet compile the latest version from source or
C) install ndiswrapper and use a windows driver

hopefully you wont have to do C, it can be a real pain in the *** when it doesn't work correctly and its generally not as good as native linux drivers anyways. I'm about 95% sure this has to do with a driver though, thats usually what it is when it says "UNCLAIMED" and lists no driver.

---

### Post by alphacrux on 2008-03-26
It seems your card doesn't work well with native linux drivers, you need to install and use madwifi or ndiswrapper. Here's one page for instructions on how to use [[COLOR="Blue"]ndiswrapper[/COLOR]]("http://ubuntuforums.org/showthread.php?t=512828&highlight=acer+aspire+3680"). There are many more posts about this topic in the forums, and even more on google. If it doesn't work right away I wouldn't be deterred, most people have to troubleshoot ndiswrapper a bit before they get it to work.

---

