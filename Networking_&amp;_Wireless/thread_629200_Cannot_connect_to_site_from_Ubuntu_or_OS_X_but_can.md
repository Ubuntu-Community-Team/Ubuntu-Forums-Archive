---
title: "Cannot connect to site from Ubuntu or OS X but can from Windows"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by Samizdata on 2007-12-02
I'm trying to set up my work VPN on my Gutsy box and it looks like everything is set up correctly.

The weird issue is -

When I try to even traceroute from either my Gutsy box or my OS X 10.4 box, I cannot connect to the server or even trace to it, despite DNS resolving correctly.

When I try the same trace or connection from my XP SP2 box, the trace works and I can connect.

All I can figure out is that there's something in the stacks causing them to route differently.  Of course, I could be wrong.

Any suggestions out there?

---

### Post by TheWizzard on 2007-12-02
please give us usefull information. 
how is your network setup?
what  server are you trying to connect to?
can you ping your router, etc

---

### Post by Samizdata on 2007-12-02
> **TheWizzard said:**
> please give us usefull information. 
how is your network setup?
what  server are you trying to connect to?
can you ping your router, etc

The network is a mixed static/DHCP through a Buffalo wireless router.  The three machines in question are statically assigned and hardwired.  The server is vpn01.startek.net.  I have no other apparent connectivity problems.  Sorry if I didn't make that clear.  Everything works fine, as long as it is the Windows machine.  Only the OS X and Linux boxen will not connect through to that host.  They can connect everywhere else, apparently.  The domain name does resolve correctly via DNS.

It's just the differing traces that throw me.

What other information can I provide to help?

---

### Post by TheWizzard on 2007-12-03
ok, please boot ubuntu, open a terminal and type:
```
ping 192.168.11.1
``` (i think this is the ip for buffalo routers)
and post the output here.

also type 
```
route -n
```
and post the output here.

---

### Post by Samizdata on 2007-12-05
> **TheWizzard said:**
> ok, please boot ubuntu, open a terminal and type:
```
ping 192.168.11.1
``` (i think this is the ip for buffalo routers)
and post the output here.

also type 
```
route -n
```
and post the output here.


As requested - 

```

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.732 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.610 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.615 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.688 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.607 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.621 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=0.661 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=0.621 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=0.715 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=0.614 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=0.857 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=0.620 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=0.621 ms

--- 192.168.1.1 ping statistics ---
13 packets transmitted, 13 received, 0% packet loss, time 12000ms
rtt min/avg/max/mdev = 0.607/0.660/0.857/0.071 ms

```

(That's the proper IP as configured.)

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

And there we go.  Please again keep in mind that I don't seem to have any other real connectivity issues on this.  In fact I am posting from this same connection.  What's confusing me is why anything *nix based won't connect, but a Windows box will...

---

### Post by TheWizzard on 2007-12-05
ok, that's clear.

now try to ping 64.233.183.147 and [www.google.com](www.google.com)

---

### Post by TheWizzard on 2007-12-05
/etc/resolv.conf should contain something like:


nameserver 194.109.104.104
nameserver 194.109.6.66

---

### Post by Samizdata on 2007-12-07
> **TheWizzard said:**
> ok, that's clear.

now try to ping 64.233.183.147 and [www.google.com](www.google.com)

```

PING www.l.google.com (64.233.167.104) 56(84) bytes of data.
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=1 ttl=243 time=16.1 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=2 ttl=243 time=16.8 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=3 ttl=243 time=16.0 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=4 ttl=243 time=14.5 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=5 ttl=243 time=13.5 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=6 ttl=243 time=13.1 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=7 ttl=243 time=16.6 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=8 ttl=243 time=16.5 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=9 ttl=243 time=13.3 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=10 ttl=243 time=16.8 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=11 ttl=243 time=12.8 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=12 ttl=243 time=14.5 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=13 ttl=243 time=14.4 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=14 ttl=243 time=16.1 ms

--- www.l.google.com ping statistics ---
14 packets transmitted, 14 received, 0% packet loss, time 12998ms
rtt min/avg/max/mdev = 12.879/15.121/16.898/1.441 ms

```

And...

```

PING 64.233.183.147 (64.233.183.147) 56(84) bytes of data.
64 bytes from 64.233.183.147: icmp_seq=1 ttl=237 time=128 ms
64 bytes from 64.233.183.147: icmp_seq=2 ttl=237 time=128 ms
64 bytes from 64.233.183.147: icmp_seq=3 ttl=237 time=127 ms
64 bytes from 64.233.183.147: icmp_seq=4 ttl=237 time=128 ms
64 bytes from 64.233.183.147: icmp_seq=6 ttl=237 time=127 ms
64 bytes from 64.233.183.147: icmp_seq=7 ttl=237 time=127 ms
64 bytes from 64.233.183.147: icmp_seq=8 ttl=237 time=129 ms
64 bytes from 64.233.183.147: icmp_seq=9 ttl=237 time=127 ms
64 bytes from 64.233.183.147: icmp_seq=10 ttl=237 time=127 ms
64 bytes from 64.233.183.147: icmp_seq=11 ttl=237 time=127 ms
64 bytes from 64.233.183.147: icmp_seq=12 ttl=237 time=130 ms
64 bytes from 64.233.183.147: icmp_seq=13 ttl=237 time=128 ms

--- 64.233.183.147 ping statistics ---
13 packets transmitted, 12 received, 7% packet loss, time 12099ms
rtt min/avg/max/mdev = 127.485/128.318/130.210/0.922 ms

```

---

### Post by Samizdata on 2007-12-07
> **TheWizzard said:**
> /etc/resolv.conf should contain something like:


nameserver 194.109.104.104
nameserver 194.109.6.66

It reads...

```

search setup


nameserver 192.168.1.1


domain Samizdata.org
nameserver 63.97.220.10

```

---

### Post by TheWizzard on 2007-12-07
ok, your ubuntu box seems to be setup correctly. internet should be working ok. 

what is the address of the server you're trying to reach? can you ping the server?

---

### Post by Samizdata on 2007-12-11
> **TheWizzard said:**
> ok, your ubuntu box seems to be setup correctly. internet should be working ok. 

what is the address of the server you're trying to reach? can you ping the server?


Sorry for the delay.  Work's been killing me lately.

Yes and no.

I can ping it successfully from my two Windows boxen, but not from my Ubuntu or OS X box.

---

### Post by TheWizzard on 2007-12-11
ok, what is the excact address you're trying to reach?

and what type (protocol) of VPN is it?

---

