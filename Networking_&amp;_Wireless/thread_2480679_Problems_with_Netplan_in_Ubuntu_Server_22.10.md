---
title: "Problems with Netplan in Ubuntu Server 22.10"
date: 2022-11-06
forum: Networking &amp; Wireless
---

### Post by nick1231 on 2022-11-06
Hello.

[COLOR=#232629][FONT=-apple-system]I have problems with netplan in Ubuntu Server 22.10. IPv4 is working, _**but IPv6 network not working**_. Here is my netplan config:

[/FONT][/COLOR]```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      addresses:
        - 45.80.XX.XX/32
        - 2a03:XXXX:XX::6f0/125
        - 2a03:XXXX:XX::6f2/128
      routes:
        - to: default
          via: 10.0.0.1
          metric: 1
          on-link: true
        - to: default
          via: 2a03:XXXX:XX::6f1
          metric: 2
          on-link: true
      nameservers:
       addresses:
        - 1.1.1.1
        - 8.8.8.8
        - 2606:4700:4700::1111
        - 2001:4860:4860::8888[COLOR=#232629][FONT=-apple-system]
[/FONT][/COLOR]
```[COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]Command output: ip a; ip r; ip -6 r[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]
[/FONT][/COLOR]```
ip a
ens3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 52:54:00:XX:XX:XX brd ff:ff:ff:ff:ff:ff
    altname enp0s3
    inet 45.80.XX.XX/32 scope global ens3
       valid_lft forever preferred_lft forever
    inet6 2a03:XXXX:XX::6f2/128 scope global
       valid_lft forever preferred_lft forever
    inet6 2a03:XXXX:XX::6f0/125 scope global
       valid_lft forever preferred_lft forever
    inet6 fe80::XXXX:XX:fe82:1904/64 scope link
       valid_lft forever preferred_lft forever

ip r
default via 10.0.0.1 dev ens3 proto static metric 1 onlink
 
ip -6 r
::1 dev lo proto kernel metric 256 pref medium
2a03:XXXX:XX::6f2 dev ens3 proto kernel metric 256 pref medium
2a03:XXXX:XX::6f0/125 dev ens3 proto kernel metric 256 pref medium
fe80::/64 dev ens3 proto kernel metric 256 pref medium
default via 2a03:XXXX:XX::6f1 dev ens3 proto static metric 2 onlink pref medium
```[COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR]**Where is the error in my netplan config (IPv6)?**[COLOR=#232629][FONT=-apple-system] (And if possible, please write in more detail).[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR]

---

