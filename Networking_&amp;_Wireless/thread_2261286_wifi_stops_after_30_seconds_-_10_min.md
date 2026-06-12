---
title: "wifi stops after 30 seconds - 10 min"
date: 2015-01-17
forum: Networking &amp; Wireless
---

### Post by Dustin_Kimpel on 2015-01-17
Okay so I'm brand new to linux.  I'm using a usb wirless adapter and after a few minutes it randomly stops providing internet.  It is still says connected to the router but no internet.  After disconnecting and reconnecting the internet works for a couple min again.  I've read tons of other forums and tried it feels like hundreds of solutions but non of them worked for me.  Any help with this would be greatly appreciated.  Windows pissed me off and i'll have to go back to them if i cant get my wifi working correctly.

thanks,

Dustin Kimpel

---

### Post by kurt18947 on 2015-01-17
Hi Dustin

I think WiFi is the biggest hardware PITA in linux.  It might be a good start to tell us what wifi adapter you have.  That behavior is common in machines that have RealTek 8192xxx adapters, for one.  Do you know how to open and use a terminal?  If so and  you have an internal wifi adapter, type the following command and paste the output here:

```

lspci

``` 

If you're using a USB adapter the command would be "lsusb" instead of "lspci"

In either case, the output should look something like this:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
**03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)**
05:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)

```

The bolded line is my WiFi adapter. I don't spend much time here of late. There are several people here that are Wifi experts, I am not one.  Once we know what adapter you have, someone may have a suggestion on how to proceed.

---

### Post by Dustin_Kimpel on 2015-01-17
Thank you so much for the help.  Here is what I get typing lsusb:



dustin@LivingRoom:~$ lsusb
Bus 002 Device 003: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dustin@LivingRoom:~$

---

### Post by Dustin_Kimpel on 2015-01-18
Any help anyone? :/

---

### Post by tgalati4 on 2015-01-19
Sometimes USB dongles get bent and the pins get broken internally.  That is consistent with wifi failing on an intermittent basis.  Try using a USB extension cable or using a different USB port on the computer.  Placement of the dongle is important.  If your computer is under a desk with a bunch of wires, that will cause interference.

---

