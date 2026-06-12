---
title: "NetworkManager and RT61 wifi"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by cruizer on 2006-08-23
are they compatible? i haven't had success getting my notebook's RT61 wifi to work with networkmanager. but it works OK with ubuntu's built in network config tool. it's just I'd like to use NetworkManager so that i can easily slide into other networks when I bring my notebook out of the house.

anybody who's had success getting networkmanager to work with RT61? i have a feeling it doesn't recognize the "ra0" interface name...

---

### Post by stinerman on 2006-08-23
Correct.

The ralink chipsets have a different way of doing WPA/WPA2/etc than most others.  For this reason, they are not compatable.

If you must use NetworkManager for whatever reason, you'll probably have to use ndiswrapper in conjunction with wpa_supplicant (if needed).  I'm almost positive that ndiswrapper works with NetworkManager.

[Mark Wallis and Ivo von Doorn]("http://rt2400.sourceforge.net") are working on a new driver that will use wpa_supplicant and will be "standardized" to work with other 3rd party tools.

---

### Post by cruizer on 2006-08-23
thanks for the quick reply :) i guess i'll have to wait for edgy eft for that...

---

### Post by BrendanM on 2006-11-24
Do we have any idea when this might be released? I'm already running edgy and it's not in there (actually edgy broke the dapper rt61 drivers). If this is going to be ready soon, I'll save myself the hassle of using ndiswrapper. Windows binaries on Linux seems like asking for trouble.

---

