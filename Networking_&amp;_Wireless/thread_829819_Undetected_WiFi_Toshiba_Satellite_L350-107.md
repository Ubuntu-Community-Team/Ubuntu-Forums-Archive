---
title: "Undetected WiFi Toshiba Satellite L350-107"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by Skerit on 2008-06-15
A friend just bought a Toshiba L350-107, we're going to take it with us on our trip to Sweden next week, and unfortunately it has been a VERY bumpy ride.

Biggest problem is WiFi: linux won't detect anything. I have no idea what wifi device it is because toshiba doesn't think this information is useful to its users.

This is my lspci:

```
skerit@KIP-DU-LIS:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

```

---

### Post by Skerit on 2008-06-15
Apparantly, the wifi device is on some USB buss (because lspci shows nothing, but lsusb DOES show it)

To make it clear, the Toshiba Satellite L350-107 laptop has a realtek wifi device.

I'm using these drivers: Realtek Semiconductor Corporation	Windows XP 32 Bit	6.1226.1004.2007, as shown by ndiswrapper:

net8187b : driver installed
	device (0BDA:8197) present


I got them from here on the toshiba website
[http://be.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/download_drivers_bios.jsp?LNG=10&service=BE](http://be.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/download_drivers_bios.jsp?LNG=10&service=BE)

So I finally detected the wifi card, now I only hope I'll actually get a connection out of it! I'll test it asap. I must say I do not like Toshiba at all, finding this information was a tedious process and, not even their site knows what driver I need, even after I had to specify what my serial number was and all!

---

