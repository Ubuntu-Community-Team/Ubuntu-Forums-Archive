---
title: "Network will not autostart on boot"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by Cushie on 2008-10-07
Using Xubuntu 8.04 and Intel3945 wifi and I use auto login.  I have checked my network settings but have to use terminal and 'sudo /etc/init.d/ networking restart' after bootup to get the network to connect.

What files should I check to get the network to connect automatically on boot up?

This is my /etc/network/interfaces file:-

[I][SIZE="2"]auto lo
iface lo inet loopback


auto wlan0
iface wlan0 inet static
address 192.168.1.8
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key s:a............q
wireless-essid DYNA


iface eth0 inet static
address 192.168.1.6
netmask 255.255.255.0
gateway 192.168.1.[/SIZE][/I]

---

