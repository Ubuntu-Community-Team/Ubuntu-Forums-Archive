---
title: "how to disable IPv6 dynamic link local"
date: 2014-07-13
forum: Networking &amp; Wireless
---

### Post by clearski on 2014-07-13
I am trying to configure a host using dual stack (IPv4 and IPv6).

I setup a static IPv6 address in /etc/network/interfaces:

```
iface eth0 inet6 static
        address fe80:a:a:1::2
        netmask 64
        gateway fe80:a:a:1::1
```

However, *ifconfig* shows that I have both a dynamic and a static link local IPv6 address. The first uses EUI to create the Interface ID and I don't want that even on the local segment.

```
eth0      Link encap:Ethernet  HWaddr 00:25:22:XX:XX:XX  
          inet6 addr: fe80::225:22ff:feXX:XXX/64 Scope:Link
          inet6 addr: fe80:a:a:1::2/64 Scope:Link
```

Autoconfiguration is disabled in /etc/sysctl.conf

```
net.ipv6.conf.all.autoconf = 0
```

It's the first IPv6 host in the network, no IPv6 router (even though a gateway is specified in the *interfaces* file).

Any idea about how can I disable the dynamic autoconf for the link local?

Thank you.

---

