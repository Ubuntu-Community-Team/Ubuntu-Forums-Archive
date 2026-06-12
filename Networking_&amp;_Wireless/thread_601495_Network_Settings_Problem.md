---
title: "Network Settings Problem"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by Krishnan on 2007-11-03
Hi. When i logged in to ubuntu today I found a strange problem.My network settings were empty
The Connection tab which i configured previously contained none items. Even the general, DNS Tab, Host became empty.
Plz urgent help

---

### Post by Krishnan on 2007-11-03
Plz help guys

---

### Post by Krishnan on 2007-11-04
Members: 421,264. No one ready to help at all

---

### Post by Krishnan on 2007-11-04
when i type this command 
sudo gedit /etc/networking/interfaces
I get the following output
auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 10.12.81.63
netmask 255.255.255.0
gateway 10.12.81.1




auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp











auto eth1

auto eth0

---

