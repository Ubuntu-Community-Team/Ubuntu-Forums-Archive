---
title: "ralink rt2500"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by ledmauro on 2007-03-04
Hello!I'm italian and i have a wireless with chipset Ralink rt2500. I do function this wireless by these command:
sudo iwconfig ra0 essid NETGEAR
sudo iwpriv ra0 set AuthMode=WPAPSK
sudo iwpriv ra0 set EncrypType=TKIP
sudo iwpriv ra0 set WPAPSK="*******"
sudo dhclient ra0
How I can do launch these command in auto at startup?Thanks and By!

---

### Post by mojoman on 2007-03-17
Hi,

Have a look at your etc/network/interfaces. On my server (running on ralink 2500) I got the following:

```
auto lo
iface lo inet loopback

iface ra0 inet static
wireless-key [mywepkey]
wireless-essid [myessid].
address [myipaddress]
netmask [mynetmask]
gateway [mygateway]

auto ra0
```

Everything withing the [brackets] you should replace with whatever values you have. My server connect at startup. Note that I use static IP and you might prefer dynamic.

/mojoman

---

