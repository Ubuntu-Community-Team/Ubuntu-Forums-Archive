---
title: "xubuntu lan wont connect"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by oisuxx on 2008-01-27
i fixed this problem using a thread before but i cant find it anymore.
basically i had to find a file and edit it so it says

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto ath0
#iface ath0 inet dhcp

but i forgot what file it was i had to gedit it and i remember it was hidden or something.
once i saved this with a live boot-up i had to re-start and it worked great.
does anyone know what file or the post that im looking for?

thank you in advance!

---

### Post by sisco311 on 2008-01-27
the file is /etc/network/interfaces
```
gksu mousepad /etc/network/interfaces
```

you don't need to reboot, just restart your network:
```
sudo /etc/init.d/networking restart
```

---

### Post by oisuxx on 2008-01-27
hrmm seems its not working. i tried to imput those things and it still wont connect.
what a pain hahaha

does anyone know a better easier way to get the network working?
i dont wanna imput anything cause this is for a friend and he obviously wont have the same ip's as me.

---

