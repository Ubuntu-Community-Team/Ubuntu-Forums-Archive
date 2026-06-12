---
title: "ethernet power management"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by darrenleeweber on 2007-10-15
My question is about how to configure power management for an ethernet device.  I've noticed on some windows drivers that there are options for putting ethernet devices to sleep.  I am running a headless box and I need the ethernet device always on.  I found the device disappeared overnight from the LAN, so I checked the router listing of attached devices and it was not there.  The machine was still powered up and the general power managment is setup for a desktop machine (put the monitor to sleep after 10 mins).  Should I change this general config?  I don't see any options to modify power management for the ethernet device in particular.

I have a new installation of Fiesty from the i386 live desktop CD on a DELL precision 450 machine with a single Intel(R) Xeon(TM) CPU 2.40GHz, 2.5 Gb RAM, 120 Gb HD, etc:

dweber@weber-desktop:~$ lspci 
00:00.0 Host bridge: Intel Corporation E7505 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation E7505/E7205 PCI-to-AGP Bridge (rev 03)
00:02.0 PCI bridge: Intel Corporation E7505 Hub Interface B PCI-to-PCI Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34GL [Quadro FX 500/600 PCI] (rev a1)
02:1c.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 04)
02:1d.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 04)
02:1e.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 04)
02:1f.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 04)
03:0e.0 Ethernet controller: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) (rev 01)
05:0d.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
05:0d.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:0e.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)

---

