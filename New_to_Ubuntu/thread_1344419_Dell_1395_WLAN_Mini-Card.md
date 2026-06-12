---
title: "Dell 1395 WLAN Mini-Card"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by rih29 on 2009-12-02
I need some desperate help with this; my Dell Inspiron 1525 works fine with Ubuntu except the wireless card; the 1395 WLAN Mini-Card. I've tried as many guides as I can find on these forums and the internet in general, and none of them seem to work at all. I can do this to help you out:

when I type in lspci,
I get...
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

It's a BCM4312, and I've tried some guides for that too, and still nothing... I don't understand what I'm doing wrong, hopefully someone can guide me through this personally D:

---

### Post by bkratz on 2009-12-02
> **rih29 said:**
> I need some desperate help with this; my Dell Inspiron 1525 works fine with Ubuntu except the wireless card; the 1395 WLAN Mini-Card. I've tried as many guides as I can find on these forums and the internet in general, and none of them seem to work at all. I can do this to help you out:
802.11b/g (rev 01)
[/code]

It's a BCM4312, and I've tried some guides for that too, and still nothing... I don't understand what I'm doing wrong, hopefully someone can guide me through this personally D:



I will do some looking, but it doesn't look good so far. If you look at the table here

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

In the table it shows:


14e4:4312
supported (802.11g only)
BCM4312 802.11a/b/g
b43
14e4:4312
not supported - ID is duplicated
BCM4312 802.11b/g
b43


two listing for the BCM4312 and it appears that yours is the one which uses the terminology "not supported". Not sure what this really means though. It may be possible with ndiswrapper or some other way, but it will take some looking.

I think it would be worth trying

lspci -vnn | grep 14e4

in the terminal to verify which one you have.

---

### Post by rih29 on 2009-12-03
Hi, thanks for the reply. Here's my output:

```

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```

---

### Post by rih29 on 2009-12-03
Update: SOLVED! I ended up having to activate drivers; it automatically connected after doing so. :)

---

### Post by sandyd on 2009-12-03
> **rih29 said:**
> I need some desperate help with this; my Dell Inspiron 1525 works fine with Ubuntu except the wireless card; the 1395 WLAN Mini-Card. I've tried as many guides as I can find on these forums and the internet in general, and none of them seem to work at all. I can do this to help you out:

when I type in lspci,
I get...
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```It's a BCM4312, and I've tried some guides for that too, and still nothing... I don't understand what I'm doing wrong, hopefully someone can guide me through this personally D:
the card is actually a broadcom one, so you will need to install
*bcm43xx*-[I]fwcutter

and let it automatically download and install the drivers for you.
[/I]

---

