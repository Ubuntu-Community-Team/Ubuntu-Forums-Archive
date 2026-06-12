---
title: "Iptables"
date: 2014-07-25
forum: Networking &amp; Wireless
---

### Post by littleghost on 2014-07-25
I need some function of iptables. I tried some solution but not success.

My machine act as a router with 3 network interface cards.
```
eth0
192.168.0.1/24
eth1
192.168.1.1/24
eth2
192.168.2.1/24
```

I already enable routing, then my network working fine. Every machine can reach other.
Now i need to block some traffic with iptables:

01: (No need anymore!)
02: Prohibit ping request from the network connected to eth1 to any network.
03: Forward all HTTP traffic come from eth1 to Squid Proxy (installed on this router, had ip address 192.168.1.1:3128)

Thank in advance!

---

### Post by TheFu on 2014-07-25
So - what have you tried?

---

### Post by SeijiSensei on 2014-07-25
For (1)
```
iptables -A FORWARD -i eth0 -j REJECT
```
forbids traffic arriving on eth0 from being forwarded to another interface.

For (2)
```
iptables -A INPUT -p icmp -i eth1 -j REJECT
```
That blocks all ICMP traffic arriving on eth1.  However ping is just one of the ICMP services.  If you want to block pings, but enable other ICMP traffic, you'll have to study the iptables manual page.

For (3)
```
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128
```

---

### Post by littleghost on 2014-07-28
Thank you, [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195"). I have just use your command, then have some feedback:
01: not try because i don't need it any more.
02: i tried, but it only drop ping request from machine A (in network connected to eth1) to the router machine. The router still forward ping request to other network if destination of ping request is not itself. I thinking very much then decide add one more rule like this:
> iptables -A FORWARD -i eth1 -p icmp --icmp-type 8 -j DROP

then now, it work ferfectly.
03: work like a charm

Thank you very much!

---

