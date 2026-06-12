---
title: "network"
date: 2014-06-28
forum: Networking &amp; Wireless
---

### Post by Azharul_islam on 2014-06-28
dear ,
i have completed ethanet with ip4 setting. my internet option shows connected but mozilla and apps store pages show server not found. hence i can not use internet.

---

### Post by praseodym on 2014-06-28
Hi,
please open a terminal with CTRL+ALT+T and show the outputs of:
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
```
How do you connect? Is it a router or a single modem?

---

