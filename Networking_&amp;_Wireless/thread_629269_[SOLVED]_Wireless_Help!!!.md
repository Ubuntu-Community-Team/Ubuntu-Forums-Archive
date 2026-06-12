---
title: "[SOLVED] Wireless Help!!!"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by Lord DarkPat on 2007-12-02
My wireless an't working. U should have guesses it by now. :lolflag: Everything was working fine until today morning. I fired up my lappy and saw that it couldn't find any networks. So, I thought it needed some time. I went, had a bath and when I came back, IT WASN't working!!!! I checked network setting and saw that THE INTERFACE WAS DISABLED!!!! And what's worse, it wouldn't even enable. So I tried manual config, but to no avail. I need wireless. BAD!! I will be ever grateful for ur help.

---

### Post by daengbo on 2007-12-02
In order to help, we need more details. Please give the output of 
lspci
and
lsusb
Was your wireless working after install, or did you have to go through any special steps? Are you using a linux kernel module or ndiswrapper? etc. Give us something to work with.

---

### Post by Lord DarkPat on 2007-12-02
lspci:
> 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

lsusb:
> Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems)
Bus 002 Device 001: ID 0000:0000

My wireless worked out-of-the-box when I first installed. It was working fine for 1 month, till today!! I can't enable the interface. Whenever I enable, it goes back to disabled for some reason!!!
In case u wanted to know, here is the lshw -C network output
>  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:83:34:85
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

---

### Post by phimurh on 2007-12-02
Many people have to install firmware for their wireless cards in ubuntu

---

### Post by Lord DarkPat on 2007-12-02
For some vague reason, it worked after I rebooted from winBLOWS.
fIRST time that bunch of crap has been useful. Billy, thank u for the first time

---

