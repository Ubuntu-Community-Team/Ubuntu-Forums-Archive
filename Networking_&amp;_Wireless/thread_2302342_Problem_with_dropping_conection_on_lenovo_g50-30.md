---
title: "Problem with dropping conection on lenovo g50-30"
date: 2015-11-09
forum: Networking &amp; Wireless
---

### Post by Nicolas_Castro on 2015-11-09
Hi people! after solving the problem of not having wireless in the lenovo when i installed Ubuntu ( [http://ubuntuforums.org/showthread.php?t=2291922](http://ubuntuforums.org/showthread.php?t=2291922) ) I still have problems with the internet conection that drops every minute. Can you help me please?

---

### Post by chili555 on 2015-11-09
Please run and post, from a terminal:```
lspci -nnk | grep 0280 -A2
lsmod | grep -e b43 -e wl
```Thanks.

---

