---
title: "fprobe &amp; stealth interface"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by luccom on 2008-02-01
Help !

I need to setup a netflow probe to monitor the network. I tried using fprobe with a interface in promiscuous mode 

This is how I configured the interface in /etc/network/interfaces

```
auto eth2
iface eth2 inet manual
        up ifconfig $IFACE 0.0.0.0 up
        up ip link set $IFACE promisc on
        down ip link set $IFACE promisc off
        down ifconfig $IFACE down

```

Is it possible that fprobe only work if there is a IP attached to the interface ? 
I don't have any available IP for that network and I still need to monitor it.

---

