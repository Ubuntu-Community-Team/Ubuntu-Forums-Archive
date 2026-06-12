---
title: "Problem with getting IPv6 to work."
date: 2023-11-15
forum: Networking &amp; Wireless
---

### Post by wyckedjester on 2023-11-15
I'm trying to get IPv6 configured on my Ubuntu box and I can't seem to get it to work. Here are the details:


Version: Ubuntu 22.04.2 LTS
Behind a Zyxel C3000Z CenturyLink router.

$> cat 00-installer-config.yaml
network:
  ethernets:
    enp2s0:
      dhcp4: false
      dhcp6: false
      addresses: [192.168.1.32/24, 2602:47:2269:77ff::0020/56]
      nameservers:
        addresses: [192.168.1.1, 2001:428::1, 2001:428::2]
      routes:
        - to: default
          via: 192.168.1.1
        - to: "::/0"
          via: "2602:47:2269:77ff::0001"
          on-link: true
  version: 2


$> ip -6 a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 state UNKNOWN qlen 1000
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 state UP qlen 1000
    inet6 2602:61:73eb:2c00:8e89:a5ff:fe64:de9e/64 scope global mngtmpaddr noprefixroute
       valid_lft forever preferred_lft forever
    inet6 fd00::8e89:a5ff:fe64:de9e/64 scope global mngtmpaddr noprefixroute
       valid_lft forever preferred_lft forever
    inet6 2602:47:2269:77ff::20/56 scope global
       valid_lft forever preferred_lft forever
    inet6 fe80::8e89:a5ff:fe64:de9e/64 scope link
       valid_lft forever preferred_lft forever

$> ip -6 route
::1 dev lo proto kernel metric 256 pref medium
2602:47:2269:7700::/56 dev enp2s0 proto kernel metric 256 pref medium
2602:61:73eb:2c00::/64 dev enp2s0 proto ra metric 1024 pref medium
2602:61:73eb:2c00::/64 via fe80::5683:3aff:fe7d:63d2 dev enp2s0 proto ra metric 1024 pref high
fd00::/64 dev enp2s0 proto ra metric 1024 pref medium
fd00::/64 via fe80::5683:3aff:fe7d:63d2 dev enp2s0 proto ra metric 1024 pref high
fe80::/64 dev enp2s0 proto kernel metric 256 pref medium
default proto static metric 1024 pref medium
        nexthop via 2602:47:2269:77ff::1 dev enp2s0 weight 1 onlink
        nexthop via fe80::5683:3aff:fe7d:63d2 dev enp2s0 weight 1


$> ping6 -c 3 2602:47:2269:77ff::0001
PING 2602:47:2269:77ff::0001(2602:47:2269:77ff::1) 56 data bytes
From 2602:47:2269:77ff::20 icmp_seq=1 Destination unreachable: Address unreachable
From 2602:47:2269:77ff::20 icmp_seq=2 Destination unreachable: Address unreachable
From 2602:47:2269:77ff::20 icmp_seq=3 Destination unreachable: Address unreachable

--- 2602:47:2269:77ff::0001 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2033ms

IPv6 info from router:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293069&stc=1[/IMG]

I'm hooked up directly to the router so there's no other hardware that could be interfering.  Any ideas as to why I can't ping the router?  TIA!!

---

