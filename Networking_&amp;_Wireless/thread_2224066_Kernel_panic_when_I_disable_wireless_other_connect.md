---
title: "Kernel panic when I disable wireless: other connectivity problems Dell Latitude E6410"
date: 2014-05-14
forum: Networking &amp; Wireless
---

### Post by Richard_Doughman on 2014-05-14
Good morning all,

I have been running Ubuntu 12.04 on a Dell Latitude E6410 for about six months, and until recently I had no problems with the wireless connection.  Last week (maybe after an update, though I don't remember a specific trigger) the wireless connection began to cut out periodically.  

When I try to reconnect by disabling the wireless to then re-enable it, the system enters into kernel panic.  Sometimes, when I restart, the wireless connection doesn't even appear.  My wired connection has continued to function throughout.      

I am relatively inexperienced with Linux and would appreciate some trouble shooting suggestions.

Thank you,

Richard

---

### Post by praseodym on 2014-05-14
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```
Does LAN work?

---

