---
title: "Dhcp won't start at boot"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by octavo on 2008-06-07
My dhcp won't start at boot but manualy it works like a charm.

My interface reads

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
	pre-up wpa_supplicant -D wired -i eth0 -c /etc/wpa_supplicant/wpa_supplicant.conf
	sleep 5
	post-down killall -q dhclient wpa_supplicant

And wpa supplicant does his job which is even more confusing.

---

