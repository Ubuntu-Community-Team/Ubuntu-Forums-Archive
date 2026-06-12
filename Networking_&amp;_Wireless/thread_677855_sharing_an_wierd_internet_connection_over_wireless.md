---
title: "sharing an wierd internet connection over wireless wifi ad-hoc"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by raptor222 on 2008-01-25
Hi, I want to move to Ubuntu for some time now, and while checking that every thing on my computer will work i got stuck on a problem concerning setting up an ad-hoc network between my windows running laptop and the desktop pc (it is worth mentioning that i don't have Ubuntu installed but i tried to activate the ad-hoc network form the live CD).
never what i tried i couldn't make it work, Ubuntu recognized the wi-fi card but was unable establish a connection even when i tried to set up an ad hoc network on the laptop side.
so my question is does anyone knows how to set up an ad hoc wireless network with internet sharing between an Ubuntu machine and a windows (XP Pro sp2) without installing Ubuntu (using live CD). it is crucial that i make this work if I'm to switch to Ubuntu.

several thing you need to know:
i use an tp-link 54m wireless adapter model: TL-WN550G.
Ive already looked at:
[https://help.ubuntu.com/community/WifiDocs/Adhoc?highlight=%28ad-hoc%29](https://help.ubuntu.com/community/WifiDocs/Adhoc?highlight=%28ad-hoc%29) and
[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless?highlight=%28ad-hoc%29](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless?highlight=%28ad-hoc%29)
none of those worked for me.

---

### Post by bwtranch on 2008-01-25
Just a little tip, CAPS are like shouting and RED CAPS will get you nowhere on this forum.

---

### Post by raptor222 on 2008-01-25
_first thing:_
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
04:00.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
04:06.0 RAID bus controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (rev 13)
ubuntu@ubuntu:~$

_second thing:_
ubuntu@ubuntu:~$ lspci | grep Broadcom\ Corporation
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
ubuntu@ubuntu:~$ 

 i did some progress on my own. still the computers cant "talk" to each other but now the windows computr recognizes the Linux wifi ad hoc network

here is a link to some pics of what i did: [http://picasaweb.google.com/shaulliv/Linpic](http://picasaweb.google.com/shaulliv/Linpic)

---

