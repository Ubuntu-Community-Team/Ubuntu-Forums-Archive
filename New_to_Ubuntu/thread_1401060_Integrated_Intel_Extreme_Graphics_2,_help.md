---
title: "Integrated Intel Extreme Graphics 2, help?"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by fwin on 2010-02-07
Hi,  I just installed ubuntu 9.04 on a dell desktop optiplex g270, everything seems to be working fine except for the graphics card driver. I can not activate desktop effects, i already try to look for a driver in "system/administration/hardware drivers" but there is nothing there. I would really appreciate any help with this?

my video card is:

Integrated Intel Extreme® Graphics 2

This is what i get after entering: 
sudo lspci |more
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Inte
rface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics 
Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Cont
roller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Brid
ge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller 
(rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 0
2)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) A



thanks

---

### Post by fwin on 2010-02-07
I just installed ubuntu 9.10 and that solved the problem, compiz works like a charm

---

