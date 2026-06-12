---
title: "Wily -- Routes messed?"
date: 2015-10-25
forum: Networking &amp; Wireless
---

### Post by rpm13 on 2015-10-25
Upgraded vivid to wily yesterday
And networking is broken -- it seems routes are messed.
With pppoe(conf) I get IP but browser/apt/ping says network is unreachable

 
14.10 live booted from flash after pppoe setup. Network working
```
$ ip -d route
unicast default dev ppp0  proto boot  scope link
unicast 117.195.32.1 dev ppp0  proto kernel  scope link  src 117.195.40.157
unicast 192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.2  metric 1

```

Not working (upgraded) OS
```
$ ip -d route
unicast 117.195.32.1 dev ppp0  proto kernel  scope link  src 117.195.47.122
unicast 169.254.0.0/16 dev ppp0  proto boot  scope link  metric 1000 
```

---

### Post by howefield on 2015-10-25
Thread moved to the "*Networking & Wireless*" forum.

---

