---
title: "Using ndiswrapper but I think interfaces file is wrong"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by scottsanpedro on 2006-11-24
I have got my wireless card working on wlan0 but I need to reconfigure on every start up. My interfaces file looks like this
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid PrestonCourt
wireless-key s:palace

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface eth1 inet static
address 192.168.2.50
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid PrestonCourt
wireless-key blah blah

iface wlan0 inet static
address 192.168.2.5
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid PrestonCourt
wireless-key blah blah

auto wlan0

```

I only want to start wlano each time. Therefore what should I keep/memo out

Many thanks  Scottsanpedro

---

### Post by x64Jimbo on 2006-11-24
Put a # before each line that does stuff with eth1.

#iface eth1 inet dhcp
#wireless-essid PrestonCourt
#wireless-key s:palace

#iface eth1 inet static
#address 192.168.2.50
#netmask 255.255.255.0
#gateway 192.168.2.1
#wireless-essid PrestonCourt
#wireless-key blah blah

That should help.

---

### Post by scottsanpedro on 2006-11-24
many thanks. will do that, and report back

---

