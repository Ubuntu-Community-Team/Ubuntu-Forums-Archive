---
title: "Network card detected, onboard not"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by cpricejones on 2008-10-06
Hey I am having an odd issue with detecting my motherboard's network card. I have a separate card (ie in an expansion slot) that is working fine with no issues at all. I need to use both though :( for providing a connection to my other machine.

Ifconfig only shows the working card (eth1), and the onboard card (eth0?) does not appear in ifconfig or in lspci. the onboard card has worked in the past on older installs, but on my newest install it seems to have disappeared.

Any help would be appreciated! I can give more info :)

---

### Post by banditti on 2008-10-06
Can you post the output of lspci?  What kind of card is it?

---

### Post by cpricejones on 2008-10-06
Hi, here is my lspci:

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc R430 [Radeon X800] (PCIE) (Secondary)


The motherboard card is on a P23G PC Chips motherboard with VIA VT6103L chipset. The network card is Intel PWLA8391GT. The Intel card is what I'm using right now, and the VIA chipset has worked in the past. However, I've not been able to get them working simultaneously. :/

---

### Post by cpricejones on 2008-10-07
Sooo I borrowed another network card (some random card 3Com) and tried it. Now I have 3 total cards in my computer:

1) Intel card mentioned above
2) motherboard card mentioned above
3) New 3Com card

Oddly, the new 3Com card is eth2, and my Intel card is eth1. eth0 has officially disappeared from my system. I am able to get eth2 to accept internet connection and broadcast to eth1. This is all working fine using firestarter and dhcp3-server.

However this does not solve the initial problem ... :?

---

