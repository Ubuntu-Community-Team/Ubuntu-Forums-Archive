---
title: "configuring ipv6 routing"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by update_manager on 2008-04-20
I have a hurricane electric tunnel broker account. IPv6 access works great on my firewall/server.

I set up radvd to hand out IPv6 addresses from my assigned prefix, and enabled ipv6 routing in /etc/sysctl.conf

Clients get an IPv6 address and can resolve names
ping6 ipv6.google.com
PING ipv6.google.com(2001:4860:0:2001::68) 56 data bytes

clients can not ping or otherwise route through the firewall. Here is my radvd configuration file, any advice is appreciated.  :-)

interface eth1
{
    AdvSendAdvert on;

    MinRtrAdvInterval 3;
    MaxRtrAdvInterval 10;

    prefix 2001:470:1f07:2e::/64
    {
        AdvOnLink on;
        AdvAutonomous on;
        AdvRouterAddr off;
    };
};

---

