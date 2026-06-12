---
title: "Using openvpn and ZNC together, please help."
date: 2017-08-25
forum: Networking &amp; Wireless
---

### Post by amy.vincent on 2017-08-25
Hello friends,

I am trying to set up znc with the ability to also use openvpn, so that znc is protected by the vpn. I have set ip routes so that other services like http, telnet, etc work; however, I can't seem to wrap my head around how to allow znc to communicate with the irc server. Searching around the net has left me scratching my head, and so far burying my head in networking manuals has thus far not yielded enlightenment.

I'd really appreciate any advice anyone can give me, or if someone perhaps knows of an existing tutorial?

Thanks again!!

edit; I routed ip with below method to allow me to access public ip remotely and can, for instance, ftp or http OUT just fine... but this is where I'm stuck. ZNC just won't play with the irc server and I am suuuper stumped! I had hoped the irc server would be able to communicate with znc, but I think I am missing something vital.

ip rule add table 128 from <public ip>
ip route add table 128 to <public ip subnet> dev eth0
ip route add table 128 default via <gateway.1>

---

### Post by TheFu on 2017-08-26
Welcome to the forums.

Commands and output for 
* more /etc/lsb-release
* uname -a
* ifconfig
* route -n
please.   Also, use **code tags** (Adv Reply "#") so it is readable.

Obfuscating the data may limit responses.

Plain FTP shouldn't be used, BTW.  It is a terrible protocol for security, firewalls, and routers.

---

### Post by amy.vincent on 2017-08-26
[FONT=courier new]```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS"
```
```

Linux amy.vincent.tk 4.4.0-92-generic #115-Ubuntu SMP Thu Aug 10 09:04:33 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```
```

eth0      Link encap:Ethernet  HWaddr 00:16:3c:07:74:80  
          inet addr:5.2.64.141  Bcast:5.2.64.255  Mask:255.255.255.0
          inet6 addr: 2a04:52c0:101:98:216:3cff:fe07:7480/64 Scope:Global
          inet6 addr: 2a04:52c0:101:2eb::783d/64 Scope:Global
          inet6 addr: fe80::216:3cff:fe07:7480/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4846013 errors:0 dropped:49095 overruns:0 frame:0
          TX packets:478942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:615095174 (615.0 MB)  TX bytes:71855213 (71.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4037 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4037 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:205090 (205.0 KB)  TX bytes:205090 (205.0 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.10.30.130  P-t-P:10.10.30.130  Mask:255.255.255.192
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.30.129    128.0.0.0       UG    0      0        0 tun0
0.0.0.0         5.2.64.1        0.0.0.0         UG    0      0        0 eth0
5.2.64.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.10.30.128    0.0.0.0         255.255.255.192 U     0      0        0 tun0
128.0.0.0       10.10.30.129    128.0.0.0       UG    0      0        0 tun0
172.241.151.18  5.2.64.1        255.255.255.255 UGH   0      0        0 eth0
```

Thank you for replying to me! Remaining shielded by my VPN while being able to have znc communicate with  IRC servers is of course my goal; specifically freenode, and despite burying my head in networking manuals I'm still banging it against the desk. Starting to get a little sore.

 Also, thanks  for the tip on FTP.. I'm aware it is insecure, it was mainly used as a  test to see what the current routing was allowing me to do. <3 I really appreciate your time! [/FONT]

---

### Post by TheFu on 2017-08-27
Here's my routing table using openvpn with a commercial provider.  I'm using the stock openvpn package, just with some example .ovpn config files.  Seeing a working example is often helpful.

My subnet is 172.22.22.0/24.  .1 is the local router/gateway.  46.45.x.x is the exit node.

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.5.10.5       128.0.0.0       UG    0      0        0 tun0
0.0.0.0         172.22.22.1     0.0.0.0         UG    5      0        0 eth0
10.5.10.1       10.5.10.5       255.255.255.255 UGH   0      0        0 tun0
10.5.10.5       0.0.0.0         255.255.255.255 UH    0      0        0 tun0
46.45.177.100   172.22.22.1     255.255.255.255 UGH   0      0        0 eth0
128.0.0.0       10.5.10.5       128.0.0.0       UG    0      0        0 tun0
172.22.22.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```
I didn't have to do anything special for this to work as expected.  Your setup appears to be on the internet directly, not behind a firewall. I generally setup "servers" that allow inbound connections and "clients" which prevent inbound connection in very different ways.  Keeps things clearer in my mind.  I could never connect to 46.45.177.100 with an inbound connection to access my system.  I'd have to use a different method.  OTOH, all traffic that isn't on the same LAN will automatically exit through the 46.45.x.x IP.

I've never needed to add manual routes.  Notice how my default gateway has a metric of 5?   That is important. It is lower priority.

---

### Post by amy.vincent on 2017-08-27
Everything except for ZNC works just fine... do you run ZNC on that config?

---

### Post by TheFu on 2017-08-28
> **amy.vincent said:**
> Everything except for ZNC works just fine... do you run ZNC on that config?

Nope.  Isn't ZNC just a php webapp w/ REST interface for other clients?
Which web server are you using? Is it bound to the correct interface?  Just guessing here.

---

