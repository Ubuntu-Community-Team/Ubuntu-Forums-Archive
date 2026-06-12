---
title: "How to set up two different ip blocks on one server?"
date: 2014-02-13
forum: Networking &amp; Wireless
---

### Post by void4 on 2014-02-13
I have two different ip blocks, each with a different gateway. I'm not sure how to set up the interfaces on my server to be able to use the ips from both. Any advice?

---

### Post by sandyd on 2014-02-13
Try something like
```

auto eth0
iface eth0 inet static
address 192.168.0.222
netmask 255.255.255.0
network 192.168.0.0
gateway 192.168.0.1

auto eth0:0
iface eth0:0 inet static
address 172.16.0.222
netmask 255.255.0.0
gateway 172.16.0.1
```

---

### Post by brokenhachi on 2014-02-13
Do you only have 1 NIC on the server or are the different gateways on different physically different routers/devices which would connect to different NICs on the server? if the former, the above will work, if the latter, just change eth0:0 to eth1 maybe.

---

