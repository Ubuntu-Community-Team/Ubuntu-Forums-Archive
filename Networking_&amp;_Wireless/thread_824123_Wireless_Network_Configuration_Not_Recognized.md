---
title: "Wireless Network Configuration Not Recognized"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by wkdude18 on 2008-06-09
Ubuntu and my network connection never seem to mix well. I have Kubuntu, Linux Mint (I'm going to uninstall it soon, it's not good), and elive triple-booted on my computer. My internet connection works on the other two, and it used to work on Kubuntu. But I noticed I have no signal, so I look at my network configuration screen and it says eth0 is a wired connection, although when I set it, it was a wireless connection. I look at mey netwrok/interface/etc or something like that and it says I have a wireless connection. What gives?

Oh heres sudo vi /etc/network/interfaces

auto lo
iface lo inet loopback


iface eth1 inet dhcp
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x
wireless-key **
wireless-essid **



iface eth0 onet dhcp

---

