---
title: "Can't associate ipw2200"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by yjr on 2006-11-06
I just upgraded from dapper to edgy, and my wireless network stop working ! My conf is a Hp nx8220 equipped with ipw2200 wireless.

My router is configured with 128 bit wep encryption. What i can do is see wireless network with network manager or iwlist eth0 scann
and result are correct but whenever I try to connect to secured network it fails ](*,) . I didn't install any special drivers.

Thanks in advance for helping me out...
YJR

---

### Post by yjr on 2006-11-09
Ok I just updated drivers for ieee80211 and ipw 2200 as well as copied the last firmware. But still my card won'associate with AP.
I can see AP with iwlist, set essid but can't associate. Looking a dmesg it say link is not ready then link is ready then no ipv6 router present and link is not ready all of this for each connection tentative.

Hopefully someone has a hint ???
Thanks
YJR

---

### Post by ryu kun on 2006-11-09
if it helps, [this]("http://doc.gwos.org/index.php/Network_Manager_with_WPA") page explains how to configure ipw2200.

---

### Post by yjr on 2006-11-11
Guys I've made it just added the keyword open before my wep key /etc/network/interfaces...
So easy in fact... Found it in faq of ipw 2200 driver...

---

