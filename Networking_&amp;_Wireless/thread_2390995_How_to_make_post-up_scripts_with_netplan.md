---
title: "How to make post-up scripts with netplan?"
date: 2018-05-04
forum: Networking &amp; Wireless
---

### Post by marcus-dahlberg on 2018-05-04
I need to disable TSO offloading. How do I do this under netplan (18.04)?

I used to do it in interfaces:

auto eno1
iface eno1 inet dhcp
post-up /sbin/ethtool -K eno1 tso off

---

