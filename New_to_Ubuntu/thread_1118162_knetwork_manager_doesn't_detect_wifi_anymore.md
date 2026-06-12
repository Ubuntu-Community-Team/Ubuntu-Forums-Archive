---
title: "knetwork manager doesn't detect wifi anymore"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by Nyxanu on 2009-04-06
Hi there,

So I'm a total newbie and happily knetworkmanager has always worked fine for me for connecting to wifi.  Then about a week ago it just stopped working.  I'll check that wifi is available on my phone and it is, but my laptop doesn't see it at all.  I can still use a ethernet cable to great effect, but no more wifi.  Any help/tips would be greatly appreciated.

Thank you in advance!

P.S. I am a TOTAL newbie.

---

### Post by tjwoosta on 2009-04-09
first off you should determine which wireless card you are using


if its usb do

```
lsusb
```

if its pci do

```
lspci
```

if your not sure just do both

post the output/outputs on the forums so we can see exactly which card you have, and we might be able to help you

---

### Post by Nyxanu on 2009-04-10
Thank you, tjwoosta.



Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 003: ID 05a9:2640 OmniVision Technologies, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
lisa@nyxanu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

---

### Post by tjwoosta on 2009-04-10
well now we know that this is your wireless card

```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
```

(Intel PRO/Wireless 4965)


this is usefull information when searching for a solution

anyway i dont have any experience with this card so im probably not going to be of much help

according to what i have read the card is supposed to have native support built into the kernel, meaning it should just work without any setup (which is confirmed by your first post)

since it just stopped working on its own, its hard saying what the problem is

(its probable that some driver or something that the card depends on broke during and update or something )

here is a thread i found that might help  (of course it is a bit dated so im not sure really)

[http://ubuntuforums.org/showthread.php?t=969178]("http://ubuntuforums.org/showthread.php?t=969178")

i guess the best advice i have is to just search google and see what you can come up with  (chances are that somebody else with this card has already experienced your problem and have worked out a fix)

EDIT: also you might get better results from posters if you start a new thread and put what wireless card you have in the title

---

### Post by Nyxanu on 2009-04-12
Thank you for your reply.  I just did as you suggested and posted a new thread.  I didn't really understand the solution given in the link that you sent me :-/

---

