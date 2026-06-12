---
title: "mtu config problem"
date: 2005-04-08
forum: Networking &amp; Wireless
---

### Post by mikecar52 on 2005-04-08
I have to write ifconfig wlan0 mtu 1454 every time I boot as I don't where to put it so it  automatically takes place.  Can someone advise me.
cheers

---

### Post by lao_V on 2005-04-08
Network config file -> /etc/network/interfaces

---

### Post by philcolbourn on 2005-04-11
yes, as Iao wrote you put it into /etc/network/interfaces.

eg.

iface wlan0 inet dhcp
        name wg111/zyair
        wireless_mode managed
        wireless_essid xxxxx
        wireless_key xxxxxxxxxxxxxxxxx
        mtu 1478

auto wlan0

---

