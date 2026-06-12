---
title: "WPA Access Issue : Beginner Help"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by rochak on 2008-02-24
Hi guyz,

I need some help: (this is

When I boot my Gutsy, my wireless connection (WPA Personal) is not automatically detected. But I can click on the network manager icon and then do a manual connection to connect to my network with no problems.

How do I automate it? Do I need to install the wpa supplement package for this even when I can connect it manually? For information, my present interfaces file is the default one


------------------------------------
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

------------------------------------------


I am using ndiswrapper to get my card working and I must say it was a very painful process.. so I hope I don't do anything which screws that part up.. hence I am hesitant in installing wpa supplement unless it is necessary..

Any help will be deeply appreciated.

Thanks

---

### Post by spd106 on 2008-02-25
It should just connect automatically. Make sure that you have roaming mode enabled for the interface in the Network capplet.

Wpa_supplicant is already installed, both Network Manager and Network-Admin use it in the background.

If you need to have static address setting then you might want to have a look at the Wireless Security sticky.

---

