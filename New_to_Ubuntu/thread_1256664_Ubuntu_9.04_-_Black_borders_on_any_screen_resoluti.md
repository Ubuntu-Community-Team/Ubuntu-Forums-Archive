---
title: "Ubuntu 9.04 - Black borders on any screen resolution that isnt 1440x900. PLEASE HELP!"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by Spoken on 2009-09-02
Basically, Im running Ubuntu 9.04 on a Dell inspiron 1420 Laptop

MY PROBLEM:

My default resolution is 1440x900. which works fine, but, it poses 2 problems. (UPDATE: I CANNOT reconfigure xserver, the latest releases of ubuntu use a auto-detection system for displays)

1)ANYTIME i changed my screen resolution to anything but 1440x900, it changes, but with 1 inch black borders around all 4 sides, making the GUI itself rather small.....with really big stuff in it. lol.  how do i fix my intel drivers...and or reconfigure my display....

2)its rather small, id like the screen to be a bit bigger for some games. Also i cant play any games that are fullscreen


MY SPECS:

=Duel 2.2ghz processor
=2 gb ram
=intel media accelorator x2100 (im pretty sure its x2100)..but it is indeed a intel card.


OUTPUT FROM "lSPCI":

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
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
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


---

### Post by scorp123 on 2009-09-02
> **Spoken said:**
>  1)ANYTIME i changed my screen resolution to anything but 1440x900, it changes, but with 1 inch black borders around all 4 sides Is that a laptop? Then it's in the BIOS settings. "Zoom display", "Scale display" or something like that. If that option is not set then the laptop will display lower resolutions "as is".

If this is not a laptop then you'd have to adjust your screen's settings by going into the screen's setup menu. The option should be named in a similar way.

---

### Post by Spoken on 2009-09-02
yes it is a laptop (inspiron 1420), but i just restarted , and went to the bios, but the options you described were no where to be found.

where are they?

---

### Post by Spoken on 2009-09-03
so....where is everyone...asleep lol?

---

### Post by scorp123 on 2009-09-03
> **Spoken said:**
> so....where is everyone...asleep lol? It's 6:00 in the morning. I went to bed too early so I woke up like 2 hours ago. So yes, I'd say most people in Europe are still sleeping and across the big pond they're likely to go to bed soon. And in Asia I guess it's lunch time now? :D

---

### Post by Spoken on 2009-09-03
so can u help me find those settings in bios like you stated before?

---

### Post by scorp123 on 2009-09-03
> **Spoken said:**
> so can u help me find those settings in bios like you stated before? Yeah right, let me come to your house, make coffee for you, clean up your bed room, and read your BIOS screens for you ...

Oh wait. I won't. :D

Duuuuude. Seriously. Open the BIOS and browse through it until you find the stupid setting. Or Google around. Dell's web site might be a good start. I am sure they have product documentation and what not on their web site? There's a few things you can do yourself  :D

---

### Post by Spoken on 2009-09-03
wow, all i did was ask for your help since im not that much of a ubuntu wiz.  u dont have to get all switzerland *** hole style on me.

---

### Post by scorp123 on 2009-09-03
> **Spoken said:**
> wow, all i did was ask for your help since im not that much of a ubuntu wiz. You don't need to be a wiz of anything for this. Just read the stupid BIOS screens until you find the setting. That really isn't too much to ask for?

> **Spoken said:**
>  u dont have to get all switzerland *** hole style on me. And you don't have to be *that* lazy.

---

