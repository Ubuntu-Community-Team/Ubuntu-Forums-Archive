---
title: "Amilo Pro V3505 internet problems!"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by Teethman on 2007-02-17
My laptop would not connect to the wireless!

I went by someones advice and changed "lo" to "eth1"

I connected! However I couldn't go on the internet?!?!?

Firefox just said server not found and stuff!

It said 100% signal, 

Please help!!!!!

---

### Post by GigaVolt on 2007-03-30
> **Teethman said:**
> My laptop would not connect to the wireless!

I went by someones advice and changed "lo" to "eth1"

I connected! However I couldn't go on the internet?!?!?

Firefox just said server not found and stuff!

It said 100% signal, 

Please help!!!!!
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#  WIRELESS
auto eth1
iface eth1 inet dhcp
wireless-essid   MYNETWOTK
wireless-channel 6
wireless-mode    managed

---

