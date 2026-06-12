---
title: "Ubuntu Edgy vpn problems - ping P-t-P: sendmsg: Operation not permitted"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by edgars on 2007-01-26
Hi,

I absolutely can' t get PPTP VPN working.

I get connected:
```

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.2.163  P-t-P:192.168.2.165  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:345 (345.0 b)  TX bytes:80 (80.0 b)


```

But nothing works: 
```

PING 192.168.2.165 (192.168.2.165) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

```

I suppose that can have something to do  with a firewall. I set iptables to accept everything, but that does not help. Any other ideas what could be wrong?

P.S.  vpn from windows in vmware on the same box works perfect, go figure..

---

### Post by edgars on 2007-01-26
Problem solved

Brain starts working better after posting here :)

I put  the following in /etc/firestarter/user-pre
```

$IPT -I FORWARD 1 -s 192.168.2.0/24 -d 192.168.2.0/24 -j ACCEPT
$IPT -I OUTPUT 1 -s 192.168.2.0/24 -d 192.168.2.0/24 -j ACCEPT
$IPT -I INPUT 1 -s 192.168.2.0/24 -d 192.168.2.0/24 -j ACCEPT

```

---

