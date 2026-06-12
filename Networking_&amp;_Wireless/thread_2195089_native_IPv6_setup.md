---
title: "native IPv6 setup"
date: 2013-12-22
forum: Networking &amp; Wireless
---

### Post by mellnik on 2013-12-22
Hello I got these information from my hoster:
```
Range: 2a00:1630:2:801::/64
Gateway: 2a00:1630:2:800::1
Netmask: /56
```

I'm a bit confused but this is my first attempt:

```
iface eth0 inet6 static
address 
netmask 56
gateway 2a00:1630:2:800::1
dns-nameservers 2620:0:ccc::2 2620:0:ccd::2
#up ip -6 addr add 2a00:1630:2:801::/64 dev eth0



```
I don't know what to put at *address *and why it is 56 netmask and not 64.
Also is following required?
```
up ip -6 addr add 2a00:1630:2:801::/64 dev eth0
```

---

