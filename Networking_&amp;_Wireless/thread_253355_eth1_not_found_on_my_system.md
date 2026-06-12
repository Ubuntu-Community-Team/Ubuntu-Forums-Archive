---
title: "eth1 not found on my system"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by adonit on 2006-09-08
Hello

I just installed ubuntu server and then updated with ubuntu desktop. Everything working fine but i cant find my eth1.

After lspci

===================================

0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Contr
oller
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82
3x/A/C PIPC Bus Master IDE (rev 07)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                      oller (rev 90)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                      oller (rev 90)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                      oller (rev 90)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                      oller (rev 90)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
0000:00:11.0 ISA bridge: VIA Technologies, Inc.: Unknown device 3287
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8                      237 AC97 Audio Controller (rev 70)
0000:00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev                       7c)
0000:00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCIE Bridge
0000:00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX                       100 DDR/200 DDR] (rev b2)
0000:02:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
0000:02:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
0000:02:01.0 0403: VIA Technologies, Inc. VIA High Definition Audio Controller

:-k 
=============================================

Any idea?

---

### Post by hw-tph on 2006-09-08
You have one network controller showing up in that listing:```
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
```
This device should show up as eth0 if it is the first Ethernet network controller in the machine.

What is the problem? Do you have another card that is not recognized? If so, what hardware does it use?

Or is it the controller I listed above that doesn't work? Browse through the output of the dmesg command (type **dmesg | less**) and look for messages relating to the via-rhine module and other related info.


Håkan

---

### Post by adonit on 2006-09-08
I have two network controllers on my system. The network controller on-board (eth0) its ok. I have problem with eth1 pci (ReadyLINK RE100ATX/WOL).

---

### Post by tbonius on 2006-09-08
Do you know what module this network card requires to load?  Also.. does the kernel recognize that card is even present?

user@host# lspci -v

Do you see that card listed at all?

What modules are loaded?

user@host# lsmod 

Im sure its just a matter of loading the right module so that the card gets initialized (if there is a drive for this card).

T

---

### Post by tbonius on 2006-09-08
I am blind... I see that you did "lspci".  Is this an onboard NIC?  Is it enabled in the BIOS?

T

---

### Post by adonit on 2006-09-09
In the middle time i change the mobo with 32bit intel and two d-link lan adapters. My ubuntu working 40% faster than suse 10.1!!!
Thanks for support.

---

