---
title: "wired internet connection setup"
date: 2014-11-02
forum: Networking &amp; Wireless
---

### Post by skt.diaz on 2014-11-02
i have been using a wired broadband connection through ethernet on windows 8
i just installed ubuntu 14.10 but i have no idea how to setup the same connection. 
i copied the ipv4 addresses and entered my username and password..still cant connect
please help..
thanks..

---

### Post by praseodym on 2014-11-02
Hi,

is it a single modem or a modem/router combo? Please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
route -n
cat /etc/network/interfaces
cat /etc/resolv.conf
```
Do you try to connect via "DSL" in the network-manager applet?

---

