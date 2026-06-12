---
title: "Can't browse thru Nokia 6275 (gnome-ppp) unless gateway deleted"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by Josh123 on 2008-07-25
I have recently installed Hardy 64 bit. This is my /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth1 inet static
address 10.12.69.203
netmask 255.255.255.0
gateway 10.12.69.1
auto eth1

iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0

auto eth0

This is /etc/resolve.conf
nameserver 208.67.222.222
nameserver 208.67.220.220
search Type address
nameserver 202.144.115.4
nameserver 202.144.66.6

networking tab to configure network settings in gnome-ppp is set as below-
IP - Dynamic IP address
DNS - Automatic

I have to delete gateway if I want to connect to internet thru my Nokia 6275 by using gnome-ppp. I do not understand where the problem is.
Can anyone help?

---

