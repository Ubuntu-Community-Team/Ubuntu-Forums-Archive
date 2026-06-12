---
title: "network gateway being reset after a system reboot"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by tr333 on 2007-01-12
I set the routing gateway with:
```
sudo route add default gw xxx.xxx.xxx.xxx
```

When I reboot the server the gateway value is being reset...
ie. the /proc/net/route file is being reset to default values.

how can i set the gateway and not have to reset it after each boot?

---

### Post by Jussi Kukkonen on 2007-01-12
Not sure if this is what you wanted to know, but /etc/network/interfaces is the normal way to set network configuration details (at least if you use ifup/ifdown).

---

### Post by tr333 on 2007-01-12
i have already set "gateway xxx.xxx.xxx.xxx" in /etc/network/interfaces (xxx.xxx.xxx.xxx is my router ip)

i'm not sure why the gateway isn't being set, since the static ip address in that file seems to be set ok.


EDIT:  I modified the /etc/network/interfaces file when i switched from using dhcp to using a static ip address.  there didnt seem to be a problem when i was using dhcp.

---

