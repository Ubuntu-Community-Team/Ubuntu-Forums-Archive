---
title: "Ubuntu incorrectly reports no internet connection"
date: 2020-10-29
forum: Networking &amp; Wireless
---

### Post by samdejong86 on 2020-10-29
Hello Ubuntu forums,

Occasionally Ubuntu 18.04 will report that there's no internet connection (the icon in the top right is greyed out). Despite this, I can load webpages in firefox and pinging an address from the command line works.

The problem is that Spotify sees that there's no connection and therefore won't play any music until the problem goes away, which it does on it's own after a few minutes.

Any ideas what might cause this? I'm on a wired connection.

Thank you for your assistance,
Sam

---

### Post by pcfan1234 on 2020-10-30
Run ```
ip a
cat /etc/resolv.conf
systemd-resolve --status #you have to press arr down to see the complete output
```
and post it here.

---

### Post by samdejong86 on 2020-10-30
Thanks for the reply. Here's the output

```

sam@hal-9000:~>ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 54:04:a6:49:9c:b6 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.16/24 brd 192.168.0.255 scope global dynamic noprefixroute enp2s0
       valid_lft 509020sec preferred_lft 509020sec
    inet6 fd00:fc:8d44:5512:c1b4:685a:4930:5ba6/64 scope global temporary dynamic 
       valid_lft 535427sec preferred_lft 76754sec
    inet6 fd00:fc:8d44:5512:4863:243d:1881:1cda/64 scope global temporary deprecated dynamic 
       valid_lft 509022sec preferred_lft 0sec
    inet6 fd00:fc:8d44:5512:fc29:852:a74a:c62f/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 535427sec preferred_lft 401570sec
    inet6 fe80::f8c5:ad31:34fc:f1af/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp4s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 50:3e:aa:56:8c:eb brd ff:ff:ff:ff:ff:ff
6: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 500
    link/none 
    inet 10.240.101.7/32 scope global tun0
       valid_lft forever preferred_lft forever
    inet6 fe80::1b99:f2c:97de:622e/64 scope link stable-privacy 
       valid_lft forever preferred_lft forever


``````

sam@hal-9000:~>cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
options edns0
search hitronhub.home

``````


sam@hal-9000:~>systemd-resolve --status #you have to press arr down to see the complete output
Global
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

Link 6 (tun0)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no

Link 3 (wlp4s0)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no

Link 2 (enp2s0)
      Current Scopes: DNS
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
         DNS Servers: 192.168.0.1
          DNS Domain: ~.
                      hitronhub.home


```

---

