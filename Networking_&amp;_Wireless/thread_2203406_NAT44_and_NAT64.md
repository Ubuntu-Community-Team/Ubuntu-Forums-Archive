---
title: "NAT44 and NAT64"
date: 2014-02-03
forum: Networking &amp; Wireless
---

### Post by VITRUVIUS_JOHN_D._ on 2014-02-03
hello friends,

 i would like to ask help in setting up a NAT44 and NAT64 ubuntu router. thanks in advance.

---

### Post by SeijiSensei on 2014-02-03
What have you tried?  Is it more difficult than simply assigning both an IPv4 and an IPv6 address to each interface and turning on both IPv4 and IPv6 forwarding in /etc/sysctl.conf? 
```

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1

```
I don't understand the implications of disabling Stateless Address Autoconfiguration, but then I don't use IPv6.

---

