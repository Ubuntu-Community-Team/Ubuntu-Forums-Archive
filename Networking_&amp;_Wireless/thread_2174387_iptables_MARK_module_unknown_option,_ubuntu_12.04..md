---
title: "iptables MARK module unknown option, ubuntu 12.04.2"
date: 2013-09-14
forum: Networking &amp; Wireless
---

### Post by james47 on 2013-09-14
```

iptables -t mangle -A OUTPUT -p tcp -m tcp --dport 22 -j mark --set-mark 7
/lib/xtables/libxt_mark.so: no "mark" extension found for this protocol
iptables v1.4.12: unknown option "--set-mark"
Try `iptables -h' or 'iptables --help' for more information.

```

why cant i run this iptables command on my ubuntu 12.04.2?
google showed one good looking hint that said to update iproute2, but iproute2 doesnt exist as a package on ubuntu. the packge iproute without the 2 is uptodate.

---

### Post by james47 on 2013-09-14
looks like case is important, works with MARK.

---

