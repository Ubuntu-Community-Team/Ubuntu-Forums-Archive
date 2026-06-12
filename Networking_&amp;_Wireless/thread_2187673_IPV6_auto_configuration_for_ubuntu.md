---
title: "IPV6 auto configuration for ubuntu"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by hrisikeshsahu on 2013-11-13
Hi All,
I have a ubuntu 12.04 desktop with two Ethernet interface ( eth0 and eth1) and both the interfaces are IPv6 Enabled.

I am using this device as Target router with our Device for IPv6 certification.

requirement -
i want to enable and disable IPv6 on run time, which need to send Neighbor solicitation message for that interface IPv6 address.

I enabled autoconf for Eth1 in sysctl.conf ```
  [FONT=Ubuntu Mono]net.ipv6.conf.eth1.autoconf = 1 [/FONT]
```. But this didn't help.

Please help me . This is very urgent.

Regards

---

### Post by hrisikeshsahu on 2013-11-13
Thanks .. It is solved..My observation was incorrect.

---

