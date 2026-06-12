---
title: "wireless lan manager questions"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by twidget on 2007-03-04
Hi,
I'm using Kubuntu Edgy on my laptop and the wireless worked without me having to configure anything except the WEP. Theres only one problem. Whenever i want to connect i have to go into Wireless Assistant and manually tell it to connect. Is there a way i can get it to automatically connect on startup? Also i would rather be using KWifiManager but for some reason it seems to only work if i open Wireless Assistant and connect from there first.Is there a way to fix this? Thanks in advance.

---

### Post by twidget on 2007-03-20
::bump::

---

### Post by chili555 on 2007-03-21
May I please see /etc/network/interfaces?
Thanks.

---

### Post by twidget on 2007-04-01
sorry for the delay. heres the my etc/network/interfaces from my dapper box:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

weird i only have one ethernet port....

---

