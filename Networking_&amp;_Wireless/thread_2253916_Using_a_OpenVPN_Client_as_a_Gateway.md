---
title: "Using a OpenVPN Client as a Gateway"
date: 2014-11-23
forum: Networking &amp; Wireless
---

### Post by alex292 on 2014-11-23
Hi everybody,

i'm using ubuntu since last year and now i'm hanging for days at a problem. I hope i can find help in this forum. ;)

My situation:

I would like to run a ubuntu server at home. My problem is, that my Fiberglass-Provider is giving DS-Lite connections. So i have a static private ipv6 address and a public ipv4 address. Since my server needs a static private ipv4 address, i rented an additional root-server with a static ipv4 and ipv6 address.

My goal is now in a way to bind the ipv4 address of the root server to my home server with a VPN tunnel. This means that all connections to the root server should be completely forwarded  through the VPN tunnel to my home server. Conversely, any ipv4 connection which is outgoing from my home server should be routed through the VPN tunnel.

So i set up an OpenVPN server based on ipv6 at my home server and an OpenVPN client at the root server. This is working so far. With some entries in iptables i also realized, that every traffic which is incoming at the root server will be forwarded to my home server.
Now for days I tried desperately to create a tunnel in the opposite direction. To realize that i tried to teach the home server that he should take the home server to use the OpenVPN client as a gateway. But i had no success. Unfortunately I can only find instructions on how to use the OpenVPN server as a gateway, but not the OpenVPN client. A would very unlikely switch the OpenVPN server/client because i'm using OpenVPN also for connecting to my local network.


Here is an overview of my config:

Home server:
```

root@Homeserver:~# ifconfig
em1       Link encap:Ethernet  Hardware Adresse 00:26:xx:xx:xx:xx  
          inet Adresse:192.168.2.2  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6-Adresse: 2a00:xxxx:xxxx:xxxx:xxxx:b9ff:fe35:aad1/64 GÃ¼ltigkeitsbereich:Global
          inet6-Adresse: fe80::226:b9ff:fe35:aad1/64 GÃ¼ltigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX-Pakete:1464 Fehler:0 Verloren:0 ÃberlÃ¤ufe:0 Fenster:0
          TX-Pakete:1122 Fehler:0 Verloren:0 ÃberlÃ¤ufe:0 TrÃ¤ger:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX-Bytes:256371 (256.3 KB)  TX-Bytes:156573 (156.5 KB)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:65536  Metrik:1
          RX-Pakete:98 Fehler:0 Verloren:0 ÃberlÃ¤ufe:0 Fenster:0
          TX-Pakete:98 Fehler:0 Verloren:0 ÃberlÃ¤ufe:0 TrÃ¤ger:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX-Bytes:7670 (7.6 KB)  TX-Bytes:7670 (7.6 KB)

tun0      Link encap:UNSPEC  Hardware Adresse 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet Adresse:10.8.0.1  P-z-P:10.8.0.2  Maske:255.255.255.255
          UP PUNKTZUPUNKT RUNNING NOARP MULTICAST  MTU:1500  Metrik:1
          RX-Pakete:265 Fehler:0 Verloren:0 ÃberlÃ¤ufe:0 Fenster:0
          TX-Pakete:232 Fehler:0 Verloren:0 ÃberlÃ¤ufe:0 TrÃ¤ger:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:100 
          RX-Bytes:20157 (20.1 KB)  TX-Bytes:19245 (19.2 KB)

root@Homeserver:~# route
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
default         192.168.2.1     0.0.0.0         UG    0      0        0 em1
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
10.8.0.2        *               255.255.255.255 UH    0      0        0 tun0
192.168.2.0     *               255.255.255.0   U     0      0        0 em1

```

Root server:
```

root@vps104494:~# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:592 (592.0 B)  TX bytes:592 (592.0 B)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.10  P-t-P:10.8.0.9  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:25740 (25.7 KB)  TX bytes:27664 (27.6 KB)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:127.0.0.2  P-t-P:127.0.0.2  Bcast:0.0.0.0  Mask:255.255.255.255
          inet6 addr: 2001:xxxx:xxxx:xxxx::xxxx/56 Scope:Global
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:1049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:165831 (165.8 KB)  TX bytes:119203 (119.2 KB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:92.xxx.xxx.xxx  P-t-P:92.xxx.xxx.xxx  Bcast:92.xxx.xxx.255  Mask:255.255.255.0
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

root@vps104494:~# iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
DNAT       all  --  anywhere             92.xxx.xxx.xxx    to:10.8.0.1

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

```

What i've tried so far: I exchanged the default route of my home server to a route to the root server.  At the end the routing table was looking like this:
```

Ziel            Router          Genmask         Flags Metric Ref    Use Iface
default         10.8.0.10       0.0.0.0         UG    0      0        0 tun0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
10.8.0.2        *               255.255.255.255 UH    0      0        0 tun0
10.8.0.10       *               255.255.255.255 UH    0      0        0 tun0
192.168.2.0     *               255.255.255.0   U     0      0        0 em1

```

As I read in a wiki article about routers i enabled ipv4 forwarding at the root server and added some filter rules to iptables (but i think this was redundant because the policy is ACCEPT).

```

sysctl -w net.ipv4.ip_forward=1
iptables -A FORWARD -o tun0 -i venet0 -j ACCEPT
iptables -A FORWARD -o venet0 -i tun0 -j ACCEPT 

```

Configured like this my home server is not able to make any connection to a external network. Just the VPN and my local network is reachable.
Has anybody an idea why this doesn't work? Or maybe you can tell me some tools to find the reason? I tried tcpdump. But it couldn't find any packages neither on my home server nor on the root server.

I would be glad if somebody can give a hint.

---

### Post by alex292 on 2014-11-27
No ideas? I tried traceroute but it showed me just stars.

---

