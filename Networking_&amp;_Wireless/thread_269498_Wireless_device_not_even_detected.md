---
title: "Wireless device not even detected"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by kernco on 2006-10-01
I'm trying to get wireless to work on my Averatec 2260.  I think it has a Ralink 2500 chip in it, but I don't think it's even detecting the device.  I've tried installing the Ralink drivers, but still nothing.  Here is the output of lspci:

0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0336
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1336
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2336
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3336
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4336
0000:00:00.5 PIC: VIA Technologies, Inc.: Unknown device 5336
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7336
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
0000:00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
0000:00:0a.0 FireWire (IEEE 1394): O2 Micro, Inc.: Unknown device 00f7 (rev 02)
0000:00:0a.2 0805: O2 Micro, Inc.: Unknown device 7120 (rev 01)
0000:00:0a.3 Mass storage controller: O2 Micro, Inc.: Unknown device 7130 (rev 01)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
0000:00:11.0 ISA bridge: VIA Technologies, Inc.: Unknown device 3287
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 70)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
0000:00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
0000:00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCIE Bridge
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3230 (rev 01)
0000:05:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
0000:05:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port

Anyone see a wireless device there?  The output of iwconfig is this:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

After installing the ralink drivers, sit0 appeared, but that isn't really any help.  Where should I go from here?

Thanks,
Colin

---

### Post by gino.arias on 2007-11-22
Hi kenco

I`m experiencing the same problem. 

The wireless card we are talking about runs in USB (not PCI). so you have to put:
#lsusb 

and then you will see your device

If you figure out what the problem is please post.

Thanks

Gino

---

