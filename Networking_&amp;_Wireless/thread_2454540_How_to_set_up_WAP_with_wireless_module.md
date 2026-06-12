---
title: "How to set up WAP with wireless module?"
date: 2020-12-01
forum: Networking &amp; Wireless
---

### Post by adam-hardy on 2020-12-01
I'm running Ubuntu server 20.04LTS as a gateway, with 2 NICs already, one connected to the internal LAN and one connected to the DSL modem. My Netgear WAP on my LAN is slowly dying so I want to utilise the 802.11 wireless module on the motherboard and configure it as a wireless access point. 

It looks like netplan has some built-in functionality based on NetworkManager, but I am running the ubuntu server and don't have NetworkManager, I've got systemd-networkd

I tried installing NetworkManager and it started messing with resolvconf and stopping the server from doing its gateway stuff for the lan.

```

            wifis:
                  all-wlans:
                    # useful on a system where you know there is
                    # only ever going to be one device
                    match: {}
                    access-points:
                      "Joe's home":
                        # mode defaults to "infrastructure" (client)
                        password: "s3kr1t"
                  # this creates an AP on wlp1s0 using hostapd
                  # no match rules, thus the ID is the interface name
                  wlp1s0:
                    access-points:
                      "guest":
                         mode: ap
                         # no WPA config implies default of open
```

What approach should I take? Is it possible to create a mutant systemd-networkd and NetworkManager solution, or should I forget about netplan and try to set it up independently with hostapd?

---

