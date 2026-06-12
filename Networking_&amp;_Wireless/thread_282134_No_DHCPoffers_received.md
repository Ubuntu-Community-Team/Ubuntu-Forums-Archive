---
title: "No DHCPoffers received?"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by Sohum on 2006-10-22
I use a router (Netgear WGR614), which connects to the modem, to serve internet to my dektop and laptop.
My laptop connects fine using wifi, my desktop, running Windows, connects fine using an ethernet cable. Ubuntu also was able to connect until today: it gets an ipv6 address for eth0, and appears to be not sending any packets at all while still receiving roughly 10 KiB of data (ifconfig eth0).
After poking around a bit,
```
sudo dhclient eth0
```
gives
```
no dhcpoffers received
```
This, I think, is the crux of the matter. My router has not been modified as far as I can remember, however, so I don't know why it would suddenly decide to not offer dhcp to Ubuntu.
I have a wireless card in my desktop (which Ubuntu doesn't recognize), but my sights are lower. First, I wish to have LAN connectivity.

---

