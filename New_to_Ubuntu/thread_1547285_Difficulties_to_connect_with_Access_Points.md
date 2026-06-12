---
title: "Difficulties to connect with Access Points"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by Jaraqui on 2010-08-06
Hy people,

   I suspect that my wireless network board isn't using
engough trasmit power. Why I think so? Because when I am
far from the Access Point, it doesn't work and, for this
same Access Point, when the distance is shortened, everything
works fine.
   I think the following command shows what kind of 802.11
net board I use.

andre@andremacario-laptop:~$ lspci | grep Silicon
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

   My questions are:
   a) are there any terminal prompt commands that I can check my transmition 802.11 
      power?
   b) if the problem is this, what is the solution?
   c) if the problem isn't the transmistion power, what kind of problem is? Note: other notebooks work fine in
      the distances considered in this description;
   d) considering situation (c), what is the solution?

Other data: Notebook Sim1062, with Intel T3400, 320 Mb/HD, 4 Gb/RAM, Lucid Lynx.


Regards
Jaraqui

---

### Post by roger_1960 on 2010-08-06
Hi

Not sure about b), c) and d), but > iwconfig entered in terminal should give an output including "link quality"  This can be checked at various distances from the transmitter.  (Terminal is a command line interface found in "accessories")

---

