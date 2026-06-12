---
title: "Strange VPN behavour"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2008-05-07
Good day, everyone!
I have a strange (for me) pptp connection behavour that I really can't understand.

My provider's VPN server is 172.20.0.1 that I route via gateway 172.21.0.1, my IP is assigned via DHCP, but i see the following thing:```
$ ifconfig ppp0 | grep inet
inet addr:10.0.177.152  P-t-P:10.0.0.1  Mask:255.255.255.255
```I cannot ping 10.0.0.1 itself, but I can ping/traceroute some sites, like this one:```
$ traceroute yandex.ru
traceroute: Warning: yandex.ru has multiple addresses; using 87.250.251.11
traceroute to yandex.ru (87.250.251.11), 30 hops max, 40 byte packets
 1  10.0.0.1 (10.0.0.1)  16.080 ms  16.483 ms  4.391 ms
 2  172.20.0.129 (172.20.0.129)  15.862 ms  2.324 ms  12.400 ms
 3  msk15.msk121.transtelecom.net (217.150.61.202)  16.805 ms  11.679 ms  11.859 ms
 4  mow-b2-link.telia.net (213.248.97.173)  12.559 ms  17.461 ms  13.628 ms
 5  win-b1-link.telia.net (80.91.249.20)  31.259 ms  21.151 ms  20.920 ms
 6  yandex-ic-123531-mow-b1.c.telia.net (213.248.104.142)  22.732 ms  18.033 ms  19.814 ms
 7  hummer-vlan601.yandex.net (77.88.16.60)  30.978 ms  18.485 ms  22.552 ms
 8  einstein-vlan2.yandex.net (87.250.228.138)  310.284 ms  395.411 ms  458.204 ms
 9  yandex.ru (87.250.251.11)  113.778 ms  121.525 ms  120.626 ms
```
and cannot ping/traceroute others:```
$ traceroute apple.com
traceroute to apple.com (17.149.160.49), 30 hops max, 40 byte packets
 1  10.0.0.1 (10.0.0.1)  13.884 ms  6.589 ms  6.996 ms
 2  172.20.0.129 (172.20.0.129)  3.812 ms  7.651 ms  5.768 ms
 3  msk15.msk121.transtelecom.net (217.150.61.202)  9.495 ms  13.328 ms  19.999 ms
 4  xe-3-3.r01.londen05.uk.bb.gin.ntt.net (83.231.146.85)  70.951 ms  86.641 ms  87.631 ms
 5  xe-3-2.r01.londen03.uk.bb.gin.ntt.net (129.250.2.72)  348.100 ms  427.586 ms  250.537 ms
 6  xe-2-3-0.r22.londen03.uk.bb.gin.ntt.net (129.250.2.65)  75.015 ms  74.094 ms  70.691 ms
 7  as-0.r20.nycmny01.us.bb.gin.ntt.net (129.250.3.254)  142.749 ms  146.368 ms  146.210 ms
 8  ae-0.r21.nycmny01.us.bb.gin.ntt.net (129.250.2.26)  152.106 ms  171.711 ms  154.387 ms
 9  p64-2-0-0.r20.chcgil09.us.bb.gin.ntt.net (129.250.5.4)  194.219 ms  179.576 ms  192.066 ms
10  ae-0.r21.chcgil09.us.bb.gin.ntt.net (129.250.3.98)  176.158 ms  181.756 ms  235.183 ms
11  p64-3-1-0.r20.snjsca04.us.bb.gin.ntt.net (129.250.5.20)  248.505 ms  243.058 ms  240.279 ms
12  po-3.r03.snjsca04.us.bb.gin.ntt.net (129.250.3.234)  230.441 ms  239.509 ms  241.046 ms
13  xe-0.internap.snjsca04.us.bb.gin.ntt.net (129.250.12.82)  227.684 ms  235.691 ms  237.520 ms
14  border3.pc2-bbnet2.sje.pnap.net (66.151.144.71)  223.135 ms  227.425 ms  222.777 ms
15  * * *
16  * * *
```Is that a routing problem?

---

