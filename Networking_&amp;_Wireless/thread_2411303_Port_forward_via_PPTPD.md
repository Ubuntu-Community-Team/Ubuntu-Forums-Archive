---
title: "Port forward via PPTPD"
date: 2019-01-28
forum: Networking &amp; Wireless
---

### Post by error105-interia on 2019-01-28
Hello,
I have my own VPS that I use like VPN with port forwarding to my SmartHome (at home I have 3G without external IP).
Few days ago, I don't know why, my port forwarding stops work :/
Via PPTPD I have internet connection.
Can anybody helps repair that port forwarding ?
net.ipv4.ip_forward = 1

IPtables RC.local:
```
iptables -I INPUT -p tcp --dport 1723 -m state --state NEW -j ACCEPT
iptables -I INPUT -p gre -j ACCEPT
iptables -t nat -I POSTROUTING -o enp1s0 -j MASQUERADE
iptables -I FORWARD -p tcp --tcp-flags SYN,RST SYN -s 192.168.1.0/24 -j TCPMSS  --clamp-mss-to-pmtu

iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o enp1s0 -j MASQUERADE
iptables -A FORWARD -p tcp --syn -s 192.168.1.0/24 -j TCPMSS --set-mss 1356

iptables -t nat -A PREROUTING -p tcp -d IP_SERWERA --dport 8000 -j DNAT --to-destination 192.168.1.234:8000
```

Ifconfig:
```
enp1s0    Link encap:Ethernet  HWaddr fa:16:3e:45:c8:04
          inet addr:IP_Servera  Bcast:IP_Maski  Mask:255.255.240.0
          inet6 addr: fe80::f816:3eff:fe45:c804/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:451112 (451.1 KB)  TX bytes:60999 (60.9 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:11840 (11.8 KB)  TX bytes:11840 (11.8 KB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:192.168.1.10  P-t-P:192.168.1.234  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:9492 (9.4 KB)  TX bytes:8036 (8.0 KB)
```

Ifconfig /all on pptpd client:
```
PPP adapter VPN:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : VPN
   Physical Address. . . . . . . . . :
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 192.168.1.234(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.255
   Default Gateway . . . . . . . . . : 0.0.0.0
   DNS Servers . . . . . . . . . . . : 8.8.8.8
                                       8.8.4.4
   NetBIOS over Tcpip. . . . . . . . : Enabled
```

---

### Post by TheFu on 2019-01-29
Sorry, can't help except to say that PPTP isn't secure and hasn't been since before 2005 when it was hacked. Since 2012, hacking it has been trivial.  
* [https://www.youtube.com/watch?v=lHMJHJTdF8c](https://www.youtube.com/watch?v=lHMJHJTdF8c) - hacking any pptp in 3 minutes
* [https://www.pcworld.com/article/260012/tools_released_at_defcon_can_crack_widely_used_pptp_encryption_in_under_a_day.html](https://www.pcworld.com/article/260012/tools_released_at_defcon_can_crack_widely_used_pptp_encryption_in_under_a_day.html)
* [https://security.stackexchange.com/questions/45509/are-there-any-known-vulnerabilities-in-pptp-vpns-when-configured-properly](https://security.stackexchange.com/questions/45509/are-there-any-known-vulnerabilities-in-pptp-vpns-when-configured-properly)
> The protocol itself is no longer secure, as cracking the initial MS-CHAPv2 authentication can be reduced to the difficulty of cracking a single DES 56-bit key, which with current computers can be brute-forced in a very short time (making a strong password largely irrelevant to the security of PPTP as the entire 56-bit keyspace can be searched within practical time constraints).

Best to move to almost any other VPN technology.

---

