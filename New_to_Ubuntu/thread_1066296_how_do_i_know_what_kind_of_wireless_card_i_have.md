---
title: "how do i know what kind of wireless card i have?"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by jsf_pp on 2009-02-10
im almost sure its as easy as writing down something in terminal and pressing enter.
so, can you help me with this?

thanks!

---

### Post by avtolle on 2009-02-10
Try```
lspci
```for that, and a lot of other information that may come in handy.

---

### Post by jsf_pp on 2009-02-10
Thanks bro!

ok,

i got this:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

so i suppose this one is?
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter

because i need to know:

-the manufacturer
-the chipset = atheros (i suppose)
and
-the interfase = PCI (i think)

---

### Post by avtolle on 2009-02-10
Yes, that is the one. Which release (8.04, 8.10) do you have?

EDIT: Oops, see you have 8.10. Back in a bit.

---

### Post by avtolle on 2009-02-10
Take a look at [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default) and follow the process therein. Worked for me. If it doesn't work for you, there are some other options.

---

