---
title: "simply wireless card recommendation"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by hostage on 2007-01-10
Hello im new in ubuntu and i need some help.

Im looking for a wirelss pci card who are the most simpliest to configure under ubuntu edgy.

i have looked here [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
and i only found 2 card that i could buy. "netgear WPN311 and Linksys WMP54G" 

My router is a "d-link DIR-635" 

Simply asking, which card is most supportive for ubuntu edgy?

i don't care how much the card cost, only need a card who work out of the box or who are very very very simply to configure to a noob like me!

and from personal experience, which card do YOU recommend?

sry my english aren't very good.

---

### Post by hostage on 2007-01-10
:(

---

### Post by hostage on 2007-01-10
Please!

---

### Post by mark-nv on 2007-01-10
I've had very good luck with the linksys cards. I think it was about $50 when I bought it last year. It's a decent wireless G NIC that worked well under WindowsXP as well as ubuntu 6.06.

I had to muck about some using the command tools to figure out what was missing, Mostly stuff that forced the NIC to use the proper settings for my wireless world.

The gui tool for playing with the NIC is under the administrator section - Networking.

If's okay, but I had to hand edit the interface file. Also useful were the iwlist and iwconfig tools to get the card setup properly

In a shell, "sudo gedit /etc/network/interfaces"

The file had some leftover garbage from bringing up the PC on the wired network. I disabled the onboard wired NIC in the PCs BIOS setup. Then I took out that wired eth0 stuff and was left with the following

auto lo
iface lo inet loopback


iface ra0 inet dhcp
wireless-essid MyHomeNetwork
wireless-mode managed
wireless-key restricted SOMEVERYLONGKEYSEQUENCE000


auto ra0

Good luck!

---

### Post by ubuntu_demon on 2007-02-22
If you use WEP it probably doesn't make much difference. If you want to use WPA(2) then choose the WPN311 which has an atheros chipset.

---

