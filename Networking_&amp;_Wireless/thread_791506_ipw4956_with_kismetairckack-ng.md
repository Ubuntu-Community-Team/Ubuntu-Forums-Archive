---
title: "ipw4956 with kismet/airckack-ng"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by art_s on 2008-05-12
Hi all,

I installed aircrack-ng/kismet and some strange stuff is happening.
The card I've got is ipw4956.

When I start kismet, it runs allright, captures packets etc, but all other apps don't see network. When I quit it, network access isn't getting restored.

Another funny thing is airmon-ng.

When I do
> airmon-ng start wlan0

it goes:
> wlan0			iwl4965 - [phy0]/usr/sbin/airmon-ng: 833: cannot create /sys/class/ieee80211/phy0/add_iface: Directory nonexistent
Error for wireless request "Set Mode" (8B06) :
    SET failed on device mon0 ; No such device.
mon0: ERROR while getting interface flags: No such device

				(monitor mode enabled on mon0)

Is there something wrong with my card driver? Do I need to patch it or something?

Thanks!

---

### Post by art_s on 2008-05-12
bump

---

### Post by art_s on 2008-05-13
I think I solved the problem. Here was the solution:

1) get/make/install iw
2) get trunk copy of airckack-ng suite, make/install 

[http://www.aircrack-ng.org/doku.php?id=mac80211](http://www.aircrack-ng.org/doku.php?id=mac80211)

---

