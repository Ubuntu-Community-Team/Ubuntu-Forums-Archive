---
title: "hostap: can't see router"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by troubleman on 2006-12-03
Hello,

I have a T30 running dapper. I installed the hostap drivers in order to get the wireless card to work. The card is a Prism 2.5 Wavelan chipset. 

I added the default drivers to the blacklist acording to [this]("http://ubuntuforums.org/showthread.php?p=1735547") which seemed to do something. Before the card was registered as eth1, now I have both eth1 and wifi0. 

The problem is that the card gets no DHCP offers, even when sitting next to the wireless router. 

Should the eth1 have gone away after installing hostap and blacklisting the orinoco drivers? I've also edited my /etc/network/interfaces file to include only lo, eth0, and wifi0, but no matter what I don't get any offers.

-tm

---

### Post by apjone on 2006-12-03
copy and past your /etc/network/interfaces file here please

---

### Post by troubleman on 2006-12-03
/etc/network/interfaces is:


> auto lo
iface lo inet loopback

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto eth0
iface eth0 inet dhcp

#auto eth0

iface wifi0 inet dhcp
wireless-essid <my essid>

auto wifi0

thanks,
-tm

---

### Post by troubleman on 2006-12-05
<Bump>

---

