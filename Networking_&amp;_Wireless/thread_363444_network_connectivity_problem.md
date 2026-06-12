---
title: "network connectivity problem"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by byronical on 2007-02-16
I´m unable to connect to one network using either DHCP or a STATIC IP address but have no problems connecting to other networks using DHCP!

On the LAN with no connectivity and when DHCP is configured requests for a new IP address just timeout.

It was working prior to yesterday so I´m starting to think that the customer might of changed something on their corporate network. But then other colleagues with Windows 2000 have had no problems connecting to the same network even when using the same IP address that I´m trying to use

eth0 is my interface and I´ve already tried the following without success

1) Disabled ipv6
2) Cleared previous DHCP leases
3) Increased the DHCP timeout to 600 in dhclient.conf
4) Configured the eth0 interface using the exact configuration from another Windows 2000 node that can connect to that network

any ideas?

Thanks

---

### Post by byronical on 2007-02-21
Hi

I know it seems crazy but when I connected today to the network that I was having problems with, it just worked and now I'm back in business..... not sure what was the problem was since I hadn't changed any configuration from yesterday.

I 'm now able to ping my reach my gateway so I wonder what was preventing me in the first place??

```

byronical:[~] ip neigh 
10.200.6.1 dev eth0 lladdr 00:00:0c:07:ac:01 REACHABLE 
byronical:[~]

```

The mystery continues but at least I'm up and working again.

I'd previously verified that my Ubuntu box was able to connect to another network (using DCHP) without problems so maybe it was the clients network causing the problem but then Windows nodes didn't have any problems connecting to that particular network that I was having problems with. (any ideas?)

I'm still anxious that this problem might reoccur but I'll see how things go.

Thanks
Byron

---

