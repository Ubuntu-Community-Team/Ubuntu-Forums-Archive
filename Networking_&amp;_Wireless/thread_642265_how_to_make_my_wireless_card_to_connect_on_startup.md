---
title: "how to make my wireless card to connect on startup?"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by mkm87 on 2007-12-16
hi! I have Toshiba A110 notebook with Atheros AR5006EG wireless card. Wireless card works with restricted Atheros Hardware Access Layer (HAL) driver. only problem is that it won't activate on startup, so each time I have to execute this command to make it work:

sudo /etc/init.d/networking restart

It is really annoying, so I hope someone can help me out. Here is content of my /etc/network/interfaces file:

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wpa-driver wext
wpa-ssid NETGEAR
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 486c8619c4deaad7c85e799689406232909a69b65f0890e7dcfc9400807ba312


I'm using WPA2 on my home wireless network.
Any help will be greatly appreciated.

---

### Post by Junglizer on 2007-12-16
write some scripts, stick 'em in init.

---

### Post by Junglizer on 2007-12-16
whip open a file
```
 vi file
#!/bin/bash

<code> or <CLI commands>

:x

```
I don't know init.d contents off my head right now, and it varies quite a bit from distro to distro.

---

