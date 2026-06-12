---
title: "default gateway switching in edgy"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by grooveBiscuit on 2006-11-30
Hi,

In my office we have two (badly setup) separate networks, each network is connected to a separate broadband enabled phone line.

In my machine I have 2 NIC cards, both set up with static IPs, one connected to each network, both working fine.

Due to the way the networks are setup I sometimes need to specify which network interface I want to use as the default gateway.

In Dapper there was an option in the System -> Administration -> Networking tool which would let me choose which interface I wanted to use as the default gateway eth0 or eth1. In Edgy this option is gone.

What method can I use now to switch between default gateways? I guess I could just take down the interface I'm not using but I got used to the Dapper way of doing it.

Thanks.

---

### Post by zgornel on 2006-11-30
Try this:
```
sudo route add default netmask <netmask> gw <gateway-ip> dev <ethX-device>
```
It will change the default route to the specified device using the specified gateway.

---

### Post by grooveBiscuit on 2006-11-30
thanks zgornel!

works a treat :D

---

