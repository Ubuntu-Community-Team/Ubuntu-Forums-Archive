---
title: "getting traceroute to work"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by aresgunther on 2007-01-20
Hello.  When I try to use traceroute without any options, I get no result : 

1 * * *
2 * * *
  . . .

When I use traceroute with the ICMP option (-I) it does work.  From what I have read, the problem is that traceroute is not allowed to use the UDP or TCP port that is needed to use those kind of traceroute scans.  I want to use some other traceroute tools (like xtraceroute) that have no option for ICMP traceroute scans.  I have also tried disabling filtering on my router, but the problem seems to be from my computer.  

How can I get my computer to allow UDP or TCP traceroute scans?


ares

---

### Post by maggotbrain on 2007-01-21
Hi there,

Here are a couple of suggestions:
- Unless you have a firewall installed on your local machine, yourcomputer shouldn't be blocking udp. 
- Can you do a normal traceroute to your computers network interface? If you can do this sucessfully; then, I would look at your next hop router for possible filtering.
- By default traceroute uses port 33434, by using the -p option you can specify a different UDP port, if necessary.

---

### Post by aresgunther on 2007-01-21
I tried tracerouting my network address as well as the router on my network : 

```
<user>@daedalus:~$ traceroute 192.168.0.10
traceroute to 192.168.0.10 (192.168.0.10), 30 hops max, 40 byte packets
 1  192.168.0.10 (192.168.0.10)  0.103 ms  0.064 ms  0.037 ms

<user>@daedalus:~$ traceroute 192.168.0.1
traceroute to 192.168.0.1 (192.168.0.1), 30 hops max, 40 byte packets
 1  192.168.0.1 (192.168.0.1)  4.308 ms  4.637 ms  115.307 ms
```

and both of those seemed to work correctly.  So I tried an external address : 

```
<user>@daedalus:~$ traceroute yahoo.com
traceroute: Warning: yahoo.com has multiple addresses; using 216.109.112.135
traceroute to yahoo.com (216.109.112.135), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
  . . .
```

I also tried specifying the interface and gateway and varying the port :

```
<user>@daedalus:~$ traceroute -i ath0 -g 192.168.0.1 -p 42425 ubuntu.com
traceroute to ubuntu.com (82.211.81.166), 30 hops max, 48 byte packets
 1  * * *
 2  * * *
 . . .
```

I do not have a firewall installed, and I have also tried the previous tests with all packet filtering on the router turned off.  Any ideas?


ares

---

