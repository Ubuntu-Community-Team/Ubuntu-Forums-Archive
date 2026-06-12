---
title: "Slow download speeds Xubuntu 14.04"
date: 2014-05-11
forum: Networking &amp; Wireless
---

### Post by isaiah-courtney96 on 2014-05-11
So I've installed Xubuntu 14.04. Steam is downloading very slow. I get around 700 Kb/s while downloading a game on steam. On my Windows 7 partition I get around 7.8 Mb/s. I'm running on a desktop and my system is plugged directly into the router, so why am I getting such slow speeds?

---

### Post by praseodym on 2014-05-11
Hi, please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
ifconfig -a
lsmod
cat /etc/resolv.conf
```

---

