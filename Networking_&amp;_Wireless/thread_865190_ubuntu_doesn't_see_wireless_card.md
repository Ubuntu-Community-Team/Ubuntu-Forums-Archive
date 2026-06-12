---
title: "ubuntu doesn't see wireless card"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by bs89 on 2008-07-20
Hi I am a neewbie to Linux I am setting up my fist linux only box on a Toshiba Satellite L45 S7423 for some reason ubuntu does not recognize that I have a wireless card even installed. there is a toggle switch to turn wireless on/off however that does nothing the led does not even blink during boot I tried using the windows drivers and it says Hardware Present: no
please help
the wireless card is a realteck if that helps
thanks

---

### Post by PinkFloyd102489 on 2008-07-20
Open a terminal and enter:

```
lspci
```

and paste the output here.

---

### Post by bs89 on 2008-07-20
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)

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

05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)

05:01.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)

05:01.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)

05:01.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

as you can see there is nothing about a wireless card being in the system but i know it is there the computer was running vista before i installed ubuntu and it was able to see the wireless card so unless it went bad durning the ubuntu install proccess its in the computer and should work

---

