---
title: "macvlan and dhcp - Any experienced users?"
date: 2014-07-17
forum: Networking &amp; Wireless
---

### Post by srhadden on 2014-07-17
Is anyone familiar with using virtual macvlan interfaces and assigning them IPs through dhcp?

When I try to make these macvlan interfaces on my ubuntu machine, as soon as I attempt to call dhcp on them I get the IP, but then I can't connect to my machine through any IP. Something is getting confused.  It looks like my main eth0 interface starts showing dropped packets after running dhcp on the other macvlan interface.

    sudo ip link add link eth0 dev eth0m type macvlan mode bridge
    dhcp eth0m


Thanks

---

