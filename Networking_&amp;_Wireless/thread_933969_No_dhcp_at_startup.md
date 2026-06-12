---
title: "No dhcp at startup"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by ittiam on 2008-09-30
I had configured my system to connect to the wireless network at startup. It connects to the AP but does not get the IP address. I have to manually do a dhclient on my wireless interface after startup. It was working fine before I updated it to 8.04.

This is the contents of my /etc/network/interfaces file.

```
auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

Can somebody suggest as why am I doing wrong?

---

