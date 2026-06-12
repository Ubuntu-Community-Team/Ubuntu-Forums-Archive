---
title: "Wireless DWA 131 issues"
date: 2013-10-30
forum: Networking &amp; Wireless
---

### Post by deebailey70 on 2013-10-30
Hello all I was wondering if one of you guys could give me some help. I am new to Ubuntu. I am trying to get this wirelss card to work a Dlink Dwa 131. I can see the network but I am unable to connect. I have useed NDiwrapper and I am abe to see the network but when I connect it never seems to connect. Any help would be appreciated like I said I am new to Ubuntu.

---

### Post by praseodym on 2013-10-30
Please open a terminal with CTRL+ALT+T and show the outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Does LAN work?

---

