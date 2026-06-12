---
title: "Internet connection problems"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Stenen on 2009-11-24
hi, im quite new to configurating ubuntu. i have used ubuntu for more than a year, (and i dont intend to stop :-p)...
 
i use ubuntu 9.10 (9.04 was faster ...) 
 
at home, with a wired connection i can acces the internet, and i can acces mobila broadband, with no troubles... but i cant browse the net on my school's wireless net.
 
i can connect to the wireless internet, and i can see other computers connected to the school's net. The school has a sort of internet, which requires a login...
 
 
The problem may be the proxy, or an ISA client. i cant find out... the IT responsible here says that i should do some research on the ISA, cause he thinks the proxy works as it should...
 
i have got a error 403, something about ISA...
 

(i read on another threat, that a user wanted this info, thought you'd like that too) :-)
lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98M [GeForce G 105M] (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
0c:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
0d:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0d:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0d:00.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0d:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0d:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by blazemore on 2009-11-24
Despite a year of trying, my friend and I couldn't get Ubuntu past the ISA at school either. Something to do with a domain server? Interestringly, one distro did work although I can't remember which one... It may have been OpenSuse (No surprises there!)

So you may be out of luck. We tried literally everything, up to and including manual IP addresses and copying settings across from Windows.
We installed our own Windows XP as well (Our school PCs were locked up tight as hell) and that could get on out of the box, so it's definately an Ubuntu issue.

---

### Post by Stenen on 2009-11-26
ok, i have found out that it cant be the problem i mentioned before, cause i can plug the internet socket, type the username and password and have internet... but wired internet...


what should i do about the wireless?

---

