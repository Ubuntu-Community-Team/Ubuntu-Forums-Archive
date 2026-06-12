---
title: "mdprobe error"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by pitta on 2008-02-17
I get this error when typing mdprobe:

 modprobe mac80211
FATAL: Error inserting mac80211 (/lib/modules/2.6.22-14-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted

Running ubuntu 7.10  and Windows Vista.

The wireless does not work.


Any ideas

Thanks

---

### Post by bwhite82 on 2008-02-17
That command needs root privileges:

> sudo modprobe mac80211

---

