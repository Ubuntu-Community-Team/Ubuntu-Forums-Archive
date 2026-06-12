---
title: "Change Ephemeral Port Range"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by charlesess on 2007-06-08
Thanks to this excellent Forum I have wireless up on a dv2000 running Ububtu7.04, I can ping google.com ( name translation works), but I can't look at the site.

I'm sitting in a motel room so I have to control over the network, but it does work on my windows XP laptop. 

I think the problem is that the access point has open the Ephemeral ports used by windows ( 1024-4999) and has blocked the range used by linux.

Does anyone know how to change the Linux ephemeral port range.

---

### Post by ohioboy757 on 2007-06-08
You can check the port range with
```
sudo cat /proc/sys/net/ipv4/ip_local_port_range 
```
and alter this file to whatever value you want to use.

---

### Post by charlesess on 2007-06-08
found it /proc/sys/net/ipv4/ip_local_port_range

---

