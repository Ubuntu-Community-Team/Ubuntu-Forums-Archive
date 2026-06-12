---
title: "Speeding up boot by tweaking network configuration"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by sab0403 on 2007-08-10
See, this is my problem:```
[   42.628000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.948000] vmnet1: no IPv6 routers present
[   53.184000] vmnet8: no IPv6 routers present
[   53.524000] eth1: no IPv6 routers present
[   63.520000] ieee80211_crypt: registered algorithm 'WEP'
[   78.376000] eth1: no IPv6 routers present
```

That's a whole lot of time lost on stuff that I don't need. First off, how do I make the eth0 simply not be loaded (or checked) during boot? I have an idea that by editing the network/interfaces file I can do this, but obviously what I'm doing is *not* working. BTW, my current interfaces file:

```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp



#iface eth0 inet static
#address 192.168.1.191
#netmask 255.255.255.0
#gateway 192.168.1.1
```

What is all this ath0, wlan0? I only have an ethernet (eth0), wireless (eth1) and possibly an IEEE 1384 port (which Debian recognized as a network device, so perhaps it's here somewhere). Anyway, I'm *not using* the eth0 device at all in Ubuntu, so how can I make it stop checking it?

Those vmnet devices come from VMWare, no worries. I can fix those myself (I think). What I can't for the life of me disable is IPv6. Any ideas?

:confused:

---

### Post by spd106 on 2007-08-13
Those interface are just there for compatibility between different drivers, for instance ath0 is for Atheros based cards and wlan0 used to be popular for ndiswrapper.

Try checking the /etc/iftab for existing entries that might be forcing eth0 to be assigned to a particular NIC.

---

