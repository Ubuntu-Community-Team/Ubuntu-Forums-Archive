---
title: "SD card reader not working"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by philipballew on 2011-04-15
i have a new laptop with a internal sd card reader. the card i insert is known to work however not showing up on my computer. im running 10.10 64 bit on a dell studio 1558 with a 35-28 kernel. here is what lspci shows:
```
philip@philip-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
06:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
06:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
06:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
06:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
philip@philip-laptop:~$ 

```

---

### Post by durand on 2011-04-15
Here's how I got mine working.

[http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu/](http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu/)

---

### Post by philipballew on 2011-04-15
this doesnt work for me. but we probably have different card readers. whats a way to find the model of mine with out taking it apart?

---

### Post by coffeecat on 2011-04-15
Is this a standard SD card or a higher capacity SDHC? Some SD card readers don't work with SDHC cards in Linux. If SDHC, have you tried a standard SD card?

---

### Post by durand on 2011-04-15
You've got a:
06:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)

---

### Post by philipballew on 2011-04-15
the card i have is a SDHC card. ill go find a regular card to see if that works. but how can i tell if mr reader supports SDHC?

---

### Post by MoebusNet on 2011-04-16
One issue I've run into is whether or not the kernel has been compiled with support for the SD card reader you have. My Acer Aspire One D255 netbook, for example, needs the 2.6.37.x or newer kernel to support my SD card reader. That kernel is used in Natty Narwhal 11.04, so needless to say I am looking forward to Natty's release.

You can download the beta version of Natty (release is end-of-the month) and boot from Live-CD or USB to see whether or not your SD card reader is supported. Easy, cheap and won't screw up your current installation. Hope this helps!

EDIT: Lubuntu 11.04 supports my card reader perfectly from Live-USB :)

---

