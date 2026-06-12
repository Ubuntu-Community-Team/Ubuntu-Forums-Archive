---
title: "IPv6 working  with method=ignore"
date: 2015-12-28
forum: Networking &amp; Wireless
---

### Post by tom220 on 2015-12-28
We are trying to set our systems up to use a static IPv6 address.  In testing the functionality against NM 1.0.6 on a Yocto Poky build, we are getting a link local IPv6 address set even when we set the adapters IPv6 method to ignore.  We can access the system via SSH and access our web app via the IPV6 address.  If we change the method to manual and provide the same link-local IPV6 address (EUI-64 formatted address based on the MAC), we can no longer reach the system from the same client PCs.  Why are we getting an IPV6 address when we set method=ignore?  Why doesn't method=manual allow the same access?  

Sample IP6 address: fe80::213:95ff:fe19:7ff0/64

Sample connection file:

[ipv6]
dns-search=
ip6-privacy=0
method=ignore

Sample connection file w/method=manual:

 [ipv6]
address1=fe80::213:95ff:fe19:7ff0/64
dns-search=
ip6-privacy=0
method=ignore

---

