---
title: "wireless configuration"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by shaheru on 2009-09-11
Hello, I tried without success to access internet but I don' t manage to configure wireless, I check the configuration typing

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.



then /etc/network/interfaces:

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168...
netmask 255.255.255.0
gateway 192.168...

auto eth0


I think I have to configure the interface, but it is not clear how!!
Should I install complementary packages? (beside wireless-tools)
Thanks for your help!

---

### Post by arochester on 2009-09-11
What wireless chip do you have? 

If it's pci, open the Terminal and issue the command: lspci
What does the line about Network Adapter say?

If it's USB, open a terminal and issue the command : lsusb

Copy and paste the result here.

---

### Post by shaheru on 2009-09-11
Hi, thanks for your answer, this is the lspci response:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
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
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
02:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)

---

