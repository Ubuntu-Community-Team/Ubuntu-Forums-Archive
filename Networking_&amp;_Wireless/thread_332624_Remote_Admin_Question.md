---
title: "Remote Admin Question"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by Sweetpea on 2007-01-06
I have several computers on a network that I need to access remotely with SSH when I'm away from the office. If the router has an IP  address of 212.35.57.10, and I need to access a computer with a local IP address of 192.168.2.10, how would I go about that? Normally if I wanted to connect to a computer I'd just do, for example:

$ ssh root@212.35.57.10

However, I don't understand how to reach a computer that is on the other side of a router. If I wanted to connect to computers 192.168.2.10 and 192.168.2.11, and these were all behind a router that was 212.35.57.10, what IP address would I need to ssh to?

Thanks.

---

### Post by koenn on 2007-01-06
normally, you would do it just the same way, i.e. 
$ ssh root@192.168.2.10
$ ssh root@192.168.2.11

the actual routing is not a problem - it's the fact that with private addresses like these, from the outside you can only see 1 public address (the WAN interface of the router), and the router does a small trick called NAT (network address translation) to let two or more computers use the same public IP address. 

To go in the other direction, from the public side to the private side, you need a way to tell the router which of the pc's behind it you want to talk to. you can't use the IP address, so the trick is to use tcp port numbers
ssh (on the computers you want to reach) listens on tcp port 22. 
what you'd do is choose 2 arbitrary numbers between 1024 and 65000 (say 2200 and 2201), and tell the router that a connection on its port 2200 should be forwarded to port 22 on IP address 192.168.1.10, and a connection on its port 2201 should be forwarded to port 22 on IP address 192.168.1.11. This is called "port forwarding" or NAPT (Network Address and Port Translation)

To make it work, your ssh has to be pointed to the custom ports in stead of the default 22, so (with 212.35.57.10 as router public ip address)
ssh  -p 2200 212.35.57.10   # should take you to 192.168.1.10 (port 22, ssh)
ssh  -p 2201 212.35.57.10   # should take you to 192.168.1.11 ((port 22, ssh)

obviously, this will only work if the router knows NAT.

---

