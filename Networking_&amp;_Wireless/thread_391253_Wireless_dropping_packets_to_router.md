---
title: "Wireless dropping packets to router"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by fuddster on 2007-03-22
I'm having a strange problem that I couldn't find any advice on...

My wireless card connects to the internet, but when I ping my router it drops 25-30% of the packets.

I found that if I run 'sudo ifdown wlan0' followed by 'sudo ifup wlan0' a few times, the packets are no longer dropped.  It usually takes 3-4 times bringing it down and back up again before it works.

Here's my /etc/network/interfaces file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# Wifi
auto wlan0
iface wlan0 inet dhcp
wireless-essid Wireless_AP
wireless-key xxxxxxxxxxxxxxxxxxxxx

```

Does anyone know how to fix this at boot, so I don't have reset the connection multiple times every time?

---

### Post by fuddster on 2007-03-31
*bump*

Anyone have any ideas?  I'm still struggling with this...

---

