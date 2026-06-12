---
title: "no wifi detected when server17.10 installed"
date: 2017-12-07
forum: Networking &amp; Wireless
---

### Post by hunter0541 on 2017-12-07
when i install the ubuntu desktop 17.10, under the gui, i can chose my pcie wireless for LAN connect and finish the install. But when i install the ubuntu server 17.10, it can't find my pcie wireless, and after finish the install, the sources.list is empty. why

---

### Post by chili555 on 2017-12-07
In a server install for 17.10 and following, networking is established with netplan. Here is an example: [https://askubuntu.com/questions/976464/etc-network-interfaces-is-ignored/976497#976497](https://askubuntu.com/questions/976464/etc-network-interfaces-is-ignored/976497#976497)

Does your wireless show up here?```
iwconfig
```Or here?```
lspci -nnk | grep 0280 -A3
```

---

