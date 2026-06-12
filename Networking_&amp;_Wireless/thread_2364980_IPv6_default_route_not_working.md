---
title: "IPv6 default route not working"
date: 2017-06-30
forum: Networking &amp; Wireless
---

### Post by Aikon- on 2017-06-30
I would love some help in trying to figure this weird one out. On a fresh install of Ubuntu 16.04.2, IPv6 traffic cannot traverse my EdgeRouter Lite. I can ping other IPv6 hosts in my local network, including the ERL on its internal addresses, but I cannot ping any hosts outside my local network, including the ERL on its external address. Network configuration is via SLAAC and router advertisements from the ERL.

My basic setup is as follows:

```
Comcast gateway
&#9492;&#9472;&#9472; EdgeRouter Lite (1.9.1)
    &#9492;&#9472;&#9472; Win7 VirtualBox host
        &#9500;&#9472;&#9472; librenms (Ubuntu 16.04.2 LTS, upgraded from 16.04 LTS)
        &#9492;&#9472;&#9472; docker   (Ubuntu 16.04.2 LTS, fresh installation)
```

IPv6 has been working fine for my ERL, Win7, and librenms hosts for over a year. There are some other hosts connected directly to the ERL (like phones, laptops, desktops, Chromecasts, thermostats, etc); there are also some other VMs inside the VirtualBox host, primarily Ubuntu 16.04.2 LTS, upgraded from 16.04 LTS. IPv6 works for all of these hosts as well*.

It is only the fresh installation of Ubuntu 16.04.2 LTS on the docker host that is having a problem.
 
**librenms (working):**
 
```
root@librenms:~# ip -6 route
2601:aaaa:bbbb:cccc::/64 dev enp0s3  proto kernel  metric 256  expires 2591941sec pref medium
fd1f:xxxx:yyyy:1::/64 dev enp0s3  proto kernel  metric 256  expires 2591941sec pref medium
fe80::/64 dev enp0s3  proto kernel  metric 256  pref medium
default via fe80::46d9:e7ff:fe40:1481 dev enp0s3  proto ra  metric 1024  expires 1741sec hoplimit 64 pref medium
```

```
root@librenms:~# ping6 www.google.com
PING www.google.com(sfo03s08-in-x04.1e100.net) 56 data bytes
64 bytes from sfo03s08-in-x04.1e100.net: icmp_seq=1 ttl=54 time=10.7 ms
64 bytes from sfo03s08-in-x04.1e100.net: icmp_seq=2 ttl=54 time=10.0 ms
64 bytes from sfo03s08-in-x04.1e100.net: icmp_seq=3 ttl=54 time=9.17 ms
64 bytes from sfo03s08-in-x04.1e100.net: icmp_seq=4 ttl=54 time=10.0 ms
^C
--- www.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 9.177/10.010/10.756/0.559 ms
```
 
**docker (not working):**
 
```
root@docker:~# ip -6 route
2601:aaaa:bbbb:cccc::/64 dev enp0s3  proto kernel  metric 256  expires 2591780sec pref medium
fd1f:xxxx:yyyy:1::/64 dev enp0s3  proto kernel  metric 256  expires 2591780sec pref medium
fe80::/64 dev enp0s3  proto kernel  metric 256  pref medium
default via fe80::46d9:e7ff:fe40:1481 dev enp0s3  proto ra  metric 1024  expires 1580sec hoplimit 64 pref medium
```

```
root@docker:~# ping6 www.google.com
PING www.google.com(sfo03s01-in-x04.1e100.net) 56 data bytes
^C
--- www.google.com ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4014ms
```

```
root@docker:~# tcpdump -i enp0s3 ip6 -vvv
tcpdump: listening on enp0s3, link-type EN10MB (Ethernet), capture size 262144 bytes
07:55:28.592629 IP6 (hlim 1, next-header UDP (17) payload length: 154) fe80::d834:9471:12b4:9145.55142 > ff02::c.1900: [udp sum ok] UDP, length 146
07:55:31.834786 IP6 (flowlabel 0xbe37f, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf > sfo03s01-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 1
07:55:32.592315 IP6 (hlim 1, next-header UDP (17) payload length: 154) fe80::d834:9471:12b4:9145.55142 > ff02::c.1900: [udp sum ok] UDP, length 146
07:55:32.849973 IP6 (flowlabel 0xbe37f, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf > sfo03s01-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 2
07:55:33.849110 IP6 (flowlabel 0xbe37f, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf > sfo03s01-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 3
07:55:34.849234 IP6 (flowlabel 0xbe37f, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf > sfo03s01-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 4
07:55:35.593095 IP6 (hlim 1, next-header UDP (17) payload length: 154) fe80::d834:9471:12b4:9145.55142 > ff02::c.1900: [udp sum ok] UDP, length 146
07:55:35.849392 IP6 (flowlabel 0xbe37f, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf > sfo03s01-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 5
^C
8 packets captured
8 packets received by filter
0 packets dropped by kernel
```
 
I should also note that during the installation process, in "configuring apt", I have to cancel because it is trying to use the IPv6 addresses for the repositories and can't get through (it seems to hang forever, just like apt-get update would; not exactly Happy Eyeballs).

* Technically, I have another Ubuntu host (14.04 LTS) that has always exhibited similar but not identical behavior -- IPv6 would work on reboot, but after SomeTime(TM) would stop working. Mostly this affected apt-get updates and apt-get upgrades (requiring -o Acquire::ForceIPv4=True). However, all my 16.04 hosts hummed along with IPv6 just fine, so I assumed it was something broken in 14.04. I'm not interested in debugging that one other host -- part of the reason for spinning up a Docker host is to migrate that (and others) into containers.

---

### Post by Aikon- on 2017-06-30
I captured the following tcpdump on my router's LAN interface, filtering for icmp6. The first batch of 4 echo requests/replies is from the working host (librenms). The second batch of 4 echo requests (no replies) is from the non-working host (docker). It looks like the router is sending out NS, trying to find the docker host. Why would the router need to do this?

```
tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 262144 bytes

03:01:52.905749 IP6 (flowlabel 0x7d268, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe48:1483 > sfo07s13-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 1
03:01:52.918893 IP6 (class 0x20, flowlabel 0x7d268, hlim 54, next-header ICMPv6 (58) payload length: 64) sfo07s13-in-x04.1e100.net > 2601:aaaa:bbbb:cccc:a00:27ff:fe48:1483: [icmp6 sum ok] ICMP6, echo reply, seq 1
03:01:53.907687 IP6 (flowlabel 0x7d268, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe48:1483 > sfo07s13-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 2
03:01:53.918866 IP6 (class 0x20, flowlabel 0x7d268, hlim 54, next-header ICMPv6 (58) payload length: 64) sfo07s13-in-x04.1e100.net > 2601:aaaa:bbbb:cccc:a00:27ff:fe48:1483: [icmp6 sum ok] ICMP6, echo reply, seq 2
03:01:54.909588 IP6 (flowlabel 0x7d268, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe48:1483 > sfo07s13-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 3
03:01:54.920242 IP6 (class 0x20, flowlabel 0x7d268, hlim 54, next-header ICMPv6 (58) payload length: 64) sfo07s13-in-x04.1e100.net > 2601:aaaa:bbbb:cccc:a00:27ff:fe48:1483: [icmp6 sum ok] ICMP6, echo reply, seq 3
03:01:55.911724 IP6 (flowlabel 0x7d268, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe48:1483 > sfo07s13-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 4
03:01:55.923380 IP6 (class 0x20, flowlabel 0x7d268, hlim 54, next-header ICMPv6 (58) payload length: 64) sfo07s13-in-x04.1e100.net > 2601:aaaa:bbbb:cccc:a00:27ff:fe48:1483: [icmp6 sum ok] ICMP6, echo reply, seq 4

03:02:03.168484 IP6 (flowlabel 0x1bf05, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf > sfo07s13-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 1
03:02:03.178923 IP6 (hlim 255, next-header ICMPv6 (58) payload length: 32) fe80::46d9:e7ff:fe40:1481 > ff02::1:ff0e:bcf: [icmp6 sum ok] ICMP6, neighbor solicitation, length 32, who has 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf
          source link-address option (1), length 8 (1): 44:d9:e7:40:14:81
            0x0000:  44d9 e740 1481
03:02:04.168026 IP6 (flowlabel 0x1bf05, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf > sfo07s13-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 2
03:02:04.176364 IP6 (hlim 255, next-header ICMPv6 (58) payload length: 32) fe80::46d9:e7ff:fe40:1481 > ff02::1:ff0e:bcf: [icmp6 sum ok] ICMP6, neighbor solicitation, length 32, who has 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf
          source link-address option (1), length 8 (1): 44:d9:e7:40:14:81
            0x0000:  44d9 e740 1481
03:02:05.167162 IP6 (flowlabel 0x1bf05, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf > sfo07s13-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 3
03:02:05.176410 IP6 (hlim 255, next-header ICMPv6 (58) payload length: 32) fe80::46d9:e7ff:fe40:1481 > ff02::1:ff0e:bcf: [icmp6 sum ok] ICMP6, neighbor solicitation, length 32, who has 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf
          source link-address option (1), length 8 (1): 44:d9:e7:40:14:81
            0x0000:  44d9 e740 1481
03:02:06.167329 IP6 (flowlabel 0x1bf05, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf > sfo07s13-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 4
03:02:06.177499 IP6 (hlim 255, next-header ICMPv6 (58) payload length: 32) fe80::46d9:e7ff:fe40:1481 > ff02::1:ff0e:bcf: [icmp6 sum ok] ICMP6, neighbor solicitation, length 32, who has 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf
          source link-address option (1), length 8 (1): 44:d9:e7:40:14:81
            0x0000:  44d9 e740 1481
03:02:07.176330 IP6 (hlim 255, next-header ICMPv6 (58) payload length: 32) fe80::46d9:e7ff:fe40:1481 > ff02::1:ff0e:bcf: [icmp6 sum ok] ICMP6, neighbor solicitation, length 32, who has 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf
          source link-address option (1), length 8 (1): 44:d9:e7:40:14:81
            0x0000:  44d9 e740 1481
03:02:08.176344 IP6 (hlim 255, next-header ICMPv6 (58) payload length: 32) fe80::46d9:e7ff:fe40:1481 > ff02::1:ff0e:bcf: [icmp6 sum ok] ICMP6, neighbor solicitation, length 32, who has 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf
          source link-address option (1), length 8 (1): 44:d9:e7:40:14:81
            0x0000:  44d9 e740 1481

```

---

### Post by Aikon- on 2017-06-30
I manually forced an unsolicited Neighbour Discovery packet using [FONT=Lucida Console][COLOR="#696969"]sudo ndsend  2601:647:4400:6bf1:a00:27ff:fe0e:bcf enp0s3[/COLOR][/FONT], and *then* tried [FONT=Lucida Console][COLOR="#696969"]ping6 [www.google.com](www.google.com)[/COLOR][/FONT] again:

```
03:25:14.870801 IP6 (flowlabel 0xabaf1, hlim 255, next-header ICMPv6 (58) payload length: 32) fe80::a00:27ff:fe0e:bcf > ip6-allnodes: [icmp6 sum ok] ICMP6, neighbor advertisement, length 32, tgt is 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf, Flags [override]
          destination link-address option (2), length 8 (1): 08:00:27:0e:0b:cf
            0x0000:  0800 270e 0bcf
03:25:20.093906 IP6 (flowlabel 0xb9ca8, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf > sfo07s16-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 1
03:25:20.104771 IP6 (class 0x20, flowlabel 0xb9ca8, hlim 54, next-header ICMPv6 (58) payload length: 64) sfo07s16-in-x04.1e100.net > 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf: [icmp6 sum ok] ICMP6, echo reply, seq 1
03:25:21.096219 IP6 (flowlabel 0xb9ca8, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf > sfo07s16-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 2
03:25:21.107001 IP6 (class 0x20, flowlabel 0xb9ca8, hlim 54, next-header ICMPv6 (58) payload length: 64) sfo07s16-in-x04.1e100.net > 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf: [icmp6 sum ok] ICMP6, echo reply, seq 2
03:25:22.098867 IP6 (flowlabel 0xb9ca8, hlim 64, next-header ICMPv6 (58) payload length: 64) 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf > sfo07s16-in-x04.1e100.net: [icmp6 sum ok] ICMP6, echo request, seq 3
03:25:22.108780 IP6 (class 0x20, flowlabel 0xb9ca8, hlim 54, next-header ICMPv6 (58) payload length: 64) sfo07s16-in-x04.1e100.net > 2601:aaaa:bbbb:cccc:a00:27ff:fe0e:bcf: [icmp6 sum ok] ICMP6, echo reply, seq 3
```

So, I can make it work, but it looks like for some reason Ubuntu is not sending out Neighbour Advertisement/Discovery packets, neither unsolicited nor upon Neighbour Solicitation. Why would that be the case in a default installation?

I am out of my depth :(  Please help!

---

