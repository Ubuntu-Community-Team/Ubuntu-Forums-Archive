---
title: "Static route with Netplan"
date: 2018-08-02
forum: Networking &amp; Wireless
---

### Post by Hammi on 2018-08-02
Hi!

Yes, I read the other threads on this topic, and think I have applied what was said there. But to no avail.

What I have: A VM (ubuntu 18.04.1 server) with a dhcp4 IP.
What I want: Add a static route; the equivalent of
```
ip route add 10.9.0.0/24 via 192.168.1.100
```
What I tried: cloud-init is disabled. I have a 01-netcfg.yaml in /etc/netplan that reads:
```
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
    version: 2
    renderer: networkd
    ethernets:
        ens3:
            dhcp4: yes
            routes:
                - to: 10.9.0.0/24
                  via: 192.168.1.100
```
What happens: IP routing is not applied.
```
# ip route show
default via 192.168.1.1 dev ens3 proto dhcp src 192.168.1.113 metric 100 
192.168.1.0/24 dev ens3 proto kernel scope link src 192.168.1.113 
192.168.1.1 dev ens3 proto dhcp scope link src 192.168.1.113 metric 100
```

Debug output from netplan:
```
# netplan --debug apply
** (generate:3426): DEBUG: 14:12:09.471: Processing input file //etc/netplan/01-netcfg.yaml..
** (generate:3426): DEBUG: 14:12:09.471: starting new processing pass
** (generate:3426): DEBUG: 14:12:09.471: ens3: setting default backend to 1
** (generate:3426): DEBUG: 14:12:09.471: Generating output files..
** (generate:3426): DEBUG: 14:12:09.471: NetworkManager: definition ens3 is not for us (backend 1)
DEBUG:netplan generated networkd configuration exists, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:device lo operstate is unknown, not replugging
DEBUG:netplan triggering .link rules for lo
DEBUG:device ens3 operstate is up, not replugging
DEBUG:netplan triggering .link rules for ens3
```

Maybe I don't understand the debug output correctly, but I cannot see any error.

Thanks for any hint for where to look!

---

### Post by e-z2 on 2019-01-18
Try this:

```

network:
    version: 2
    renderer: networkd
    ethernets:
        ens3:
            dhcp4: yes
            routes:
                - to: 10.9.0.0/24
                  via: 192.168.1.100
                  on-link: true
```

---

