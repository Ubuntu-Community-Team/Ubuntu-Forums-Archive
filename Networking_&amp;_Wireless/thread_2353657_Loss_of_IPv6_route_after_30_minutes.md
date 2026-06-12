---
title: "Loss of IPv6 route after 30 minutes"
date: 2017-02-23
forum: Networking &amp; Wireless
---

### Post by phipac on 2017-02-23
Good afternoon, all. Since 14.04 (and including 16.04 and now 16.10), I have noticed this issue.  After a reboot, my IPv6 route is up just fine.  However, after 30 minutes, the default route disappears, and I have to manually add the route to the gateway again.  I have a static IPv6 address assigned via /etc/network/interfaces.  Here is some code and logging files:

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto enp4s0f0
iface enp4s0f0 inet manual
        bond-master bond0

auto enp4s0f1
iface enp4s0f1 inet manual
        bond-master bond0

auto bond0
iface bond0 inet static
        hwaddress ether 00:etc.
        address 172.16.10.100
        gateway 172.16.10.1
        netmask 255.255.254.0
        dns-search home.example.com
        dns-nameservers 127.0.0.1
        bond-mode 4
        bond-miimon 100
        bond-lacp-rate 1
        bond-slaves enp4s0f0 enp4s0f1
        bond-xmit_hash_policy encap3+4

iface bond0 inet6 static
        address 2605:aaaa:bbbb:cccc::a
        netmask 64
        gateway fe80::1
        dns-search home.example.com
        dns-nameservers ::1

```

/etc/sysctl.conf
```

net.ipv6.conf.all.accept_ra = 1
net.ipv6.conf.all.temp_prefered_lft = 86400
net.ipv6.conf.all.temp_valid_lft = 604800
net.ipv6.conf.all.use_tempaddr = 2

net.ipv6.conf.default.accept_ra = 1
net.ipv6.conf.default.temp_prefered_lft = 86400
net.ipv6.conf.default.temp_valid_lft = 604800
net.ipv6.conf.default.use_tempaddr = 2

```

```

sfixphdi@monstro:~$ route -6
Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
2605:e000:3cc0:9900::/64       [::]                       UA   256 1     3 bond0
fe80::/64                      [::]                       U    256 2     2 bond0
[::]/0                         gateway                    UGDAe 1024 8   132 bond0
[::]/0                         [::]                       !n   -1  1   138 lo
localhost/128                  [::]                       Un   0   9   102 lo
monstro/128                    [::]                       Un   0   3   119 lo
monstro/128                    [::]                       Un   0   1     0 lo
monstro/128                    [::]                       Un   0   4    21 lo
ff00::/8                       [::]                       U    256 6    87 bond0
[::]/0                         [::]                       !n   -1  1   141 lo
sfixphdi@monstro:~$ uptime
 13:45:42 up 4 min,  1 user,  load average: 1.14, 1.52, 0.76

```

```

sfixphdi@monstro:~$ route -6
Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
2605:e000:3cc0:9900::/64       [::]                       UA   256 4   136 bond0
fe80::/64                      [::]                       U    256 5    24 bond0
[::]/0                         [::]                       !n   -1  1  2674 lo
localhost/128                  [::]                       Un   0   9   690 lo
monstro/128                    [::]                       Un   0   5  1862 lo
monstro/128                    [::]                       Un   0   1     0 lo
monstro/128                    [::]                       Un   0   4   232 lo
ff00::/8                       [::]                       U    256 7   492 bond0
[::]/0                         [::]                       !n   -1  1  2676 lo
sfixphdi@monstro:~$ uptime
 15:22:30 up  1:41,  1 user,  load average: 0.93, 0.80, 0.83

```

---

