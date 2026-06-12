---
title: "Network problem"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by hyby on 2007-11-08
Hi guys, Sorry for double posting. In need of urgent solution.

I am currently having problems connecting online through my Ethernet connection. I can connect through windows via DHCP.
I went into the network settings and changed the eth1 setting from roaming to DHCP in Ubuntu. However, for some reason i still can not connect online. I also have wireless, but its turned off and left on roaming mode. 

Can i please get some advice.

---

### Post by wideback on 2007-11-09
You could open a terminal and try the following command:

```
sudo dhclient eth1
```

It should assign an IP address to your interface.

---

