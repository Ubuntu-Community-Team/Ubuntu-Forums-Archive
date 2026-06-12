---
title: "Another wireless connection problem :("
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by OzzMosiz on 2007-05-22
Having issues getting WIFI working:
Ok, reinstalled ubuntu from scratch
Manually ran:

ifconfig eth1 up
iwconfig eth1 essid name_I_gave
iwconfig eth1 key <hex_key>
dhclient eth1

/etc/network/interfaces =

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp

I have no /etc/resolv.conf

WTF is going wrong??? :'(

---

### Post by OzzMosiz on 2007-05-22
damn essid name was a dash not an underscore
Worked for a bit, rebooted and now wont work!!!
Edit: needed to rename the essid in /etc/network/interfaces - doh!!

---

