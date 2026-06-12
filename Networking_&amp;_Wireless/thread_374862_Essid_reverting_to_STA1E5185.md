---
title: "Essid reverting to STA1E5185"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by elreteipos on 2007-03-03
When I start up my computer, my essid is changed to STA1E5185 for some reason. I don't know such a wireless network, nor can I use it to connect to the internet. I always have to set the right essid and the WEP key to be able to surf the web again.

[[IMG]http://img473.imageshack.us/img473/21/iwconfiggg1.th.jpg[/IMG]]("http://img473.imageshack.us/img473/21/iwconfiggg1.jpg")

Any idea why this happens? Or better yet, how can I fix it?

---

### Post by spd106 on 2007-03-03
Is it mentioned in the /etc/network/interfaces file?

---

### Post by elreteipos on 2007-03-04
Nope. Here's /etc/network/interfaces:> auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp



iface wlan0 inet static
address 192.168.1.199
netmask 255.255.255.0
gateway 192.168.1.1

auto wlan0

---

### Post by spd106 on 2007-03-04
Insert these these lines
```
auto ath0
iface ath0 inet dhcp



iface wlan0 inet static
[COLOR="Red"]wireless-essid <your essid>[/COLOR]
[COLOR="Red"]wireless-key <your hex key>[/COLOR]
address 192.168.1.199
netmask 255.255.255.0
gateway 192.168.1.1

auto wlan0
```

It should automatically connect to your network now. You should be able to achieve this through a gui as well, I'm not familiar with KDE so I can't tell you how.

The odd thing is that usually a wireless interface will default to an essid of 'off/any', not STA1E5185.

---

### Post by elreteipos on 2007-03-06
Yup, that works. Thanks!

---

