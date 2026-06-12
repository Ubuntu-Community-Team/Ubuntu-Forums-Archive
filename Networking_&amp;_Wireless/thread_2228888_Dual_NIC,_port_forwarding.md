---
title: "Dual NIC, port forwarding"
date: 2014-06-10
forum: Networking &amp; Wireless
---

### Post by regs4 on 2014-06-10
Can't get second NIC to accept forwarded from router connections.

It works with Windows, but not with Ubuntu Server, which is 12.04.4

Things tryed so far

Two routers. Tryed them in single network - 192.168.0.1 and 192.168.0.10 connected via hub and in isolated networks 192.168.0.1 and 172.16.16.1 with only server connected to router. Routers have forwarded ports to, say, 192.168.0.2, if single network, and to, say, 192.168.0.2 and 172.16.16.2 respectively, if dual.
But so far, no matter what i only get forwarded connections from primary network. Both connections works fine and accessible inside LAN. Routers does forwards connections and they works both with Windows-based server.


In dual interfaces looks like. What else could be missed here?


```

iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
        dns-nameservers 192.168.0.1 77.88.8.8
        #gateway 192.168.0.1
        post-up route add default gw 192.168.0.1 metric 1
        pre-down route del default gw 192.168.0.1


iface eth1 inet static
       address 172.16.16.2
       netmask 255.255.255.0
       broadcast 172.16.16.255
       network 172.16.16.0
       #gateway 172.16.16.1
       post-up route add default gw 172.16.16.1 metric 2
       pre-down route del default gw 172.16.16.1

```

---

### Post by brantcgardner on 2014-06-10
If I understand you correctly, you probably just need to turn on IP forwarding.

here are many documents out there that cover this, here is [one]("http://www.networkinghowtos.com/howto/enable-ip-forwarding-on-ubuntu-13-04/") example that may help you.

---

### Post by regs4 on 2014-06-10
Forgot to say. I tryed that as well. It's set to 1.

---

### Post by brantcgardner on 2014-06-10
Okay, please show us the output of

```
ifconfig
```

and

```
route -n
```

---

### Post by regs4 on 2014-06-10
```

:~# route -n
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    1      0        0 eth0
0.0.0.0         172.16.16.1     0.0.0.0         UG    2      0        0 eth1
172.16.16.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

```

```

:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:xxx:55
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:67ff:fe6a:7d55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:61274 (61.2 KB)  TX bytes:44936 (44.9 KB)
          Interrupt:19 &#1055;&#1072;&#1084;&#1103;&#1090;&#1100;:c2400000-c2420000


eth1      Link encap:Ethernet  HWaddr 00:1e:xxx:54
          inet addr:172.16.16.100  Bcast:172.16.16.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:67ff:fe6a:7d54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:29161 (29.1 KB)  TX bytes:5898 (5.8 KB)
          Interrupt:16 &#1055;&#1072;&#1084;&#1103;&#1090;&#1100;:c2300000-c2320000


lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:518 (518.0 B)  TX bytes:518 (518.0 B)


virbr0    Link encap:Ethernet  HWaddr 92:0b:ac:66:87:bd
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


Apache, Webmin etc all set to listen to all connection. and they do work within LAN. But not being forwarded via secondary NIC. No matter which one is secondary.


```

C:\Users\Admin>ping 192.168.0.100
&#1054;&#1073;&#1084;&#1077;&#1085; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072;&#1084;&#1080; &#1089; 192.168.0.100 &#1087;&#1086; &#1089; 32 &#1073;&#1072;&#1081;&#1090;&#1072;&#1084;&#1080; &#1076;&#1072;&#1085;&#1085;&#1099;&#1093;:
&#1054;&#1090;&#1074;&#1077;&#1090; &#1086;&#1090; 192.168.0.100: &#1095;&#1080;&#1089;&#1083;&#1086; &#1073;&#1072;&#1081;&#1090;=32 &#1074;&#1088;&#1077;&#1084;&#1103;<1&#1084;&#1089; TTL=64
&#1054;&#1090;&#1074;&#1077;&#1090; &#1086;&#1090; 192.168.0.100: &#1095;&#1080;&#1089;&#1083;&#1086; &#1073;&#1072;&#1081;&#1090;=32 &#1074;&#1088;&#1077;&#1084;&#1103;<1&#1084;&#1089; TTL=64
&#1054;&#1090;&#1074;&#1077;&#1090; &#1086;&#1090; 192.168.0.100: &#1095;&#1080;&#1089;&#1083;&#1086; &#1073;&#1072;&#1081;&#1090;=32 &#1074;&#1088;&#1077;&#1084;&#1103;<1&#1084;&#1089; TTL=64
&#1054;&#1090;&#1074;&#1077;&#1090; &#1086;&#1090; 192.168.0.100: &#1095;&#1080;&#1089;&#1083;&#1086; &#1073;&#1072;&#1081;&#1090;=32 &#1074;&#1088;&#1077;&#1084;&#1103;<1&#1084;&#1089; TTL=64


C:\Users\Admin>ping 172.16.16.100
&#1054;&#1073;&#1084;&#1077;&#1085; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072;&#1084;&#1080; &#1089; 172.16.16.100 &#1087;&#1086; &#1089; 32 &#1073;&#1072;&#1081;&#1090;&#1072;&#1084;&#1080; &#1076;&#1072;&#1085;&#1085;&#1099;&#1093;:
&#1054;&#1090;&#1074;&#1077;&#1090; &#1086;&#1090; 172.16.16.100: &#1095;&#1080;&#1089;&#1083;&#1086; &#1073;&#1072;&#1081;&#1090;=32 &#1074;&#1088;&#1077;&#1084;&#1103;<1&#1084;&#1089; TTL=64
&#1054;&#1090;&#1074;&#1077;&#1090; &#1086;&#1090; 172.16.16.100: &#1095;&#1080;&#1089;&#1083;&#1086; &#1073;&#1072;&#1081;&#1090;=32 &#1074;&#1088;&#1077;&#1084;&#1103;<1&#1084;&#1089; TTL=64
&#1054;&#1090;&#1074;&#1077;&#1090; &#1086;&#1090; 172.16.16.100: &#1095;&#1080;&#1089;&#1083;&#1086; &#1073;&#1072;&#1081;&#1090;=32 &#1074;&#1088;&#1077;&#1084;&#1103;<1&#1084;&#1089; TTL=64
&#1054;&#1090;&#1074;&#1077;&#1090; &#1086;&#1090; 172.16.16.100: &#1095;&#1080;&#1089;&#1083;&#1086; &#1073;&#1072;&#1081;&#1090;=32 &#1074;&#1088;&#1077;&#1084;&#1103;<1&#1084;&#1089; TTL=64

```

---

### Post by brantcgardner on 2014-06-10
I think you may need to explain more what it is that you are trying to do that isn't working.  Also make sure you are clearly describing the involved nodes (e.g. Client at address x.x.x.x can't contact server y.y.y.y located past server/router z.z.z.z).

If you just arbitrarily created a new subnet that you are wanting packets to route to, you have to "teach" the rest of your nodes about that subnet (one way or another).  Since (as far as I can tell) you aren't talking about masquerading or equivalent, you don't just get automatic routes everywhere.

I know you said it worked with Windows but that OS automates some configuration items that you will need to take on yourself, or enable similar functionality in Ubuntu.

---

### Post by regs4 on 2014-06-10
Two router have forwarded port set up.

Ie.

Say, 
172.16.16.1 forwards 5080 port from WAN to 172.16.16.100:5080
192.168.0.1 forwards 5080 port from WAN to 192.168.0.100:5080

Both connections accept local connections, but only primary accepts forwarded from WAN connections


UFW is disabled. There is iptables. It's default, except one string that logs incoming connection. Those forwarded from second NIC are not logged at all.

```

# Generated by iptables-save v1.4.12 on Tue Jun 10 03:18:30 2014
*nat
:PREROUTING ACCEPT [2018:160389]
:INPUT ACCEPT [1886:153021]
:OUTPUT ACCEPT [423:59207]
:POSTROUTING ACCEPT [423:59207]
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE
COMMIT
# Completed on Tue Jun 10 03:18:30 2014
# Generated by iptables-save v1.4.12 on Tue Jun 10 03:18:30 2014
*mangle
:PREROUTING ACCEPT [12603:6600159]
:INPUT ACCEPT [12404:6584517]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [8281:3457917]
:POSTROUTING ACCEPT [8735:3542013]
-A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill
COMMIT
# Completed on Tue Jun 10 03:18:30 2014
# Generated by iptables-save v1.4.12 on Tue Jun 10 03:18:30 2014
*filter
:FORWARD ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -m state --state NEW -j LOG  --log-prefix "INBOUND CON.: "
-A INPUT -p udp -m udp -i virbr0 --dport 53 -j ACCEPT
-A INPUT -p tcp -m tcp -i virbr0 --dport 53 -j ACCEPT
-A INPUT -p udp -m udp -i virbr0 --dport 67 -j ACCEPT
-A INPUT -p tcp -m tcp -i virbr0 --dport 67 -j ACCEPT
-A FORWARD -m state -d 192.168.122.0/24 -o virbr0 --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT
-A FORWARD -i virbr0 -o virbr0 -j ACCEPT
-A FORWARD -o virbr0 -j REJECT
-A FORWARD -i virbr0 -j REJECT
COMMIT
# Completed on Tue Jun 10 03:18:30 2014

```

---

### Post by brantcgardner on 2014-06-10
All right, so you **are** masquerading.  You said you have two separate routers that you describe as "connected to WAN" that port-forward to this box.  When you say "WAN" are you referring to two separate connections to two separate ISPs or are you actually connecting to two different WANs (e.g. large corporate networks)?  Or is it the same WAN?

I'm just trying to understand your configuration, this is far more complex than I thought it was at first glance.

---

### Post by regs4 on 2014-06-10
Well, it's far more simplier than you think) Different ISPs. Moving from one to another actually and need some time when both would work.

---

### Post by brantcgardner on 2014-06-10
Based on your description, there is a possibility that your ISP is blocking all inbound connections; you might go check with your service agreement with them and rule that out before you continue.  It's not for sure your issue but I **have** run into that in the past and I would check before you spend too much time tweaking your configuration.

---

### Post by regs4 on 2014-06-10
That's not the case. All ports are open and they get forwarded properly from both networks if Windows machine is used instead. And no matter which NIC is used only primary, the one of first gateway accept incoming forwarded connections.

---

