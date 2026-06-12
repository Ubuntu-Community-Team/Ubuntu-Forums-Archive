---
title: "ipv6 dhcp not working to some devices"
date: 2013-12-13
forum: Networking &amp; Wireless
---

### Post by drolstad on 2013-12-13
Hello,

I have a dhcp server offering ipv4 and ipv6 addresses to devices. 

I can ping:

ping6 fe80::210:18ff:fe8a:f0f8%eth0
PING fe80::210:18ff:fe8a:f0f8%eth0(fe80::210:18ff:fe8a:f0f8) 56 data bytes
64 bytes from fe80::210:18ff:fe8a:f0f8: icmp_seq=1 ttl=64 time=24.4 ms
64 bytes from fe80::210:18ff:fe8a:f0f8: icmp_seq=2 ttl=64 time=8.49 ms
64 bytes from fe80::210:18ff:fe8a:f0f8: icmp_seq=3 ttl=64 time=8.48 ms

and offer a ipv6 dhcp address to fe80::210:18ff:fe8a:f0f8:


12:24:44.494298 IP6 fe80::210:18ff:fe8a:f0f8.546 > ff02::1:2.547: dhcp6 solicit
12:24:44.513044 IP6 fe80::221:9bff:fe90:6918.547 > fe80::210:18ff:fe8a:f0f8.546: dhcp6 advertise
12:24:47.654409 IP6 fe80::210:18ff:fe8a:f0f8.546 > ff02::1:2.547: dhcp6 request
12:24:47.654621 IP6 fe80::221:9bff:fe90:6918.547 > fe80::210:18ff:fe8a:f0f8.546: dhcp6 reply

but I do not answer fe80::225:5eff:fefb:23c2 correctly:


09:06:48.766097 IP6 fe80::225:5eff:fefb:23c2.546 > ff02::1:2.547: dhcp6 solicit
09:08:45.806607 IP6 fe80::225:5eff:fefb:23c2.546 > ff02::1:2.547: dhcp6 solicit
09:10:45.655145 IP6 fe80::225:5eff:fefb:23c2.546 > ff02::1:2.547: dhcp6 solicit


although the dhcp logs show I hear him and try:

Dec 13 09:04:41 beta dhcpd: Solicit message from fe80::225:5eff:fefb:23c2 port 546, transaction ID 0x97E2A600
Dec 13 09:04:41 beta dhcpd: Picking pool prefix 2001:420:340:be00::/56
Dec 13 09:04:41 beta dhcpd: Sending Advertise to fe80::225:5eff:fefb:23c2 port 546

and I can't ping him:
ping6 fe80::225:5eff:fefb:23c2%eth0
PING fe80::225:5eff:fefb:23c2%eth0(fe80::225:5eff:fefb:23c2) 56 data bytes
From fe80::221:9bff:fe90:6918 icmp_seq=1 Destination unreachable: Address unreachable
From fe80::221:9bff:fe90:6918 icmp_seq=2 Destination unreachable: Address unreachable

address unreachable implies routing error so I look at:
2001:420:340:ffff::/64         ::                         UAe  256 0120871 eth1
2001:420:340::/48              ::                         Ue   256 0120873 eth0
fe80::/64                      ::                         U    256 0     0 eth0
fe80::/64                      ::                         U    256 0     0 eth1
::/0                           2001:420:340:ffff::1       UG   1   0821528 eth0
::/0                           fe80::21c:fff:fe5d:fd00    UGDAe 1024 0     0 eth0
::/0                           fe80::21c:fff:fe5d:fd00    UGDAe 1024 0     1 eth1
::/0                           ::                         !n   -1  1113812040 lo
::1/128                        ::                         Un   0   4  3391 lo
2001:420:340:ffff::10/128      ::                         Un   0   11008889 lo
2001:420:340:ffff:221:9bff:fe90:6918/128 ::                         Un   0   1467573 lo
2001:420:340:ffff:221:9bff:fe90:691a/128 ::                         Un   0   1   977 lo
fe80::221:9bff:fe90:6918/128   ::                         Un   0   11018996 lo
fe80::221:9bff:fe90:691a/128   ::                         Un   0   1455642 lo
ff00::/8                       ::                         U    256 0     0 eth0
ff00::/8                       ::                         U    256 0     0 eth1
::/0                           ::                         !n   -1  1113812040 lo

and it looks ok. 

No iptables running or ufw.

Any guidance from the ipv6 experts? IS there something unusual about the fe80 link local scope that is blocking me?

---

