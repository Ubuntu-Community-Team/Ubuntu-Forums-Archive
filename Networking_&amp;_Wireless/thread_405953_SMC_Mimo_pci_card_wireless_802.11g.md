---
title: "SMC Mimo pci card wireless 802.11g"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by phira on 2007-04-10
hello every body
I have a very strange problem, here
I have bought a  SMC Mimo pci card wireless 802.11g

I plugged it on
and the first time, it worked: it was up without any manipulation and my wireless network was detected
I put a static IP on it 

at the next reboot (and all after) of my ubuntu 6.06 LTS
the system stops when booting on configuring network device

If I put off the card, my system runs OK

Does anybody have an idea for me?

> lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
0000:00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
0000:00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
0000:00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
0000:00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCIE Bridge
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
0000:02:01.0 0403: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
> uname -a
Linux phira 2.6.15-28-386 #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007 i686 GNU/Linux

---

