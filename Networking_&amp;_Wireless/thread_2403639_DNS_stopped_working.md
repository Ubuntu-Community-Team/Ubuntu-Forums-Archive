---
title: "DNS stopped working"
date: 2018-10-14
forum: Networking &amp; Wireless
---

### Post by romprod on 2018-10-14
****Hey,

So I'm getting the following error now, can anyone give me any pointers please?

```
ping: www.google.co.uk: Temporary failure in name resolution
```

My setup

```
network:
  version: 2
  renderer: networkd
#  ethernets:
#    enp3s0:
#      dhcp4: yes
  wifis:
    wlp2s0:
      access-points:
        "TP-Link_973B":
          password: "password"
      dhcp4: no
      dhcp6: no
      addresses: [192.168.0.254/24]
      gateway4: 192.168.0.1
      nameservers:
        addresses: [194.168.4.100,194.168.8.100,8.8.8.8,8.8.4.4,1.1.1.1,1.1.0.0]
  version: 2

```
Output of **systemd-resolve --status | sed -n '/DNS Servers/,/^$/p'**
```
         DNS Servers: 8.8.8.8
          DNSSEC NTA: 10.in-addr.arpa
                      16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal
                      intranet
                      lan
                      local
                      private
                      test

         DNS Servers: 194.168.4.100
                      194.168.8.100
                      8.8.8.8
                      8.8.4.4
                      1.1.1.1
                      1.1.0.0
                      fdf0:4682:8343::1
```

I have network connectivity fine

```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=43 time=25.3 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=43 time=24.1 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=43 time=22.0 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=43 time=21.3 ms
```

Ubuntu Version
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:        18.04
Codename:       bionic
```

---

### Post by him610 on 2018-10-14
Try this ```
ping -c2 google.co.uk

```

---

