---
title: "openSSL update - WEP stopped working"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by etherealNet on 2006-09-14
Hi,

   I couple of days ago there were a bunch of updates (openSSL etc.) which seems to have broken my wireless connection....I've been using wireless for many months now. I have a Dell inspiron 5160 laptop with bcom 4309 card. Any help will be greatly appreciated.

Thanks in advance.

](*,)

---

### Post by wieman01 on 2006-09-15
Post **"/etc/network/interfaces"** and we'll see... WEP should be much of a problem.

---

### Post by etherealNet on 2006-09-15
My /etc/network/interfaces file :

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid xxxxxxxxx
wireless-key (x)26 hex-digits

---

