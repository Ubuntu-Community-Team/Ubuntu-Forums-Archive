---
title: "Same SSID, Different Subnets"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by wareagle on 2008-02-29
My school has a vast wireless network of APs, all with the same SSID, but many in different subnets.  Unfortunately, my wirless card switches between APs and does not run a DHCP renew when it does this, so this causes my connection to get dropped.

Even if I run iwconfig eth1 essid <SSID> ap <a specific ap> channel <the channel it is on>, my card switches APs (and channels) after a while.

It does this even if I stay in one spot.  It is a Broadcom 4306 :( on Kubuntu Gutsy.

---

### Post by Sam Lars on 2008-02-29
dhclient will renew your address with DHCP...

---

### Post by wareagle on 2008-03-02
Yeah, but it won't do it automatically when my card changes subnets.  (Which is usually about every 5 minutes.)

Can my card be bound to a particular access point?

---

