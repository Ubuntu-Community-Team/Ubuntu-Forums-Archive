---
title: "how to remove an IPv6 route?"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by ahaitoute on 2008-11-01
Hello,

After I've connected to Sixxs, I've added the following route in the IPv6 routing table (for subnet purposes):
[PHP]sudo route -A inet6 add 2001:610:693::/48 gw 2001:610:693::1 dev eth0[/PHP]

Now I got the following IPv6 routing table:
[PHP]route -6
Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
2001:610:600:50a::/64          ::                         U    256 0     1 sixxs
2001:610:693::/48              2001:610:693::1            UG   1   0     0 eth0
2001:610:693::/48              ::                         U    256 0     2 eth0
fe80::/64                      ::                         U    256 0     0 wlan0
fe80::/64                      ::                         U    256 0     0 sixxs
fe80::/64                      ::                         U    256 0     0 eth0
::/0                           2001:610:600:50a::1        UG   1024 0     0 sixxs
::/0                           ::                         !n   -1  1    41 lo
::1/128                        ::                         Un   0   1     7 lo
2001:610:600:50a::2/128        ::                         Un   0   1    81 lo
fe80::214:a5ff:fe66:911c/128   ::                         Un   0   1     0 lo
fe80::410:600:50a:2/128        ::                         Un   0   1     0 lo
ff00::/8                       ::                         U    256 0     0 wlan0
ff00::/8                       ::                         U    256 0     0 sixxs
ff00::/8                       ::                         U    256 0     0 eth0
::/0                           ::                         !n   -1  1    41 lo
[/PHP]

Now, I would like to remove the following IPv6 route from the routing table:
2001:610:693::/48              ::                         U    256 0     2 eth0

I tried by:
[PHP]sudo route -A inet6 del 2001:610:693::/48[/PHP]

But it removes the route that I've just added:
[PHP]2001:610:693::/48              2001:610:693::1            UG   1   0     0 eth0[/PHP]

---

