---
title: "Connecting 2 ubuntu with crossover cable, unreacheable ping"
date: 2013-12-11
forum: Networking &amp; Wireless
---

### Post by PsykoMantis on 2013-12-11
Hi all,
i did just buy a fresh new ethernet crossover cable.
What i want to do is connecting two Ubuntu systems (one with 12.10 and the other with 13.04).
What i've done is this step by step: [http://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router](http://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router) 
The ip of the machine where i pinged from is192.0.0.1
here the results:

```
~$ ping 192.0.0.2
PING 192.0.0.2 (192.0.0.2) 56(84) bytes of data.
From 192.0.0.1 icmp_seq=1 Destination Host Unreachable
From 192.0.0.1 icmp_seq=2 Destination Host Unreachable
From 192.0.0.1 icmp_seq=3 Destination Host Unreachable
From 192.0.0.1 icmp_seq=4 Destination Host Unreachable
From 192.0.0.1 icmp_seq=5 Destination Host Unreachable
From 192.0.0.1 icmp_seq=6 Destination Host Unreachable
From 192.0.0.1 icmp_seq=7 Destination Host Unreachable
From 192.0.0.1 icmp_seq=8 Destination Host Unreachable
From 192.0.0.1 icmp_seq=9 Destination Host Unreachable
From 192.0.0.1 icmp_seq=10 Destination Host Unreachable
From 192.0.0.1 icmp_seq=11 Destination Host Unreachable


```


why?

p.s.
the systems recognise the connection to up, so i don't know why this. I want to know deeply what's going on. Don't be afraid to speak tecnical because i'm a computer science student.
Thanks


HERE HOW I SOLVED

my cable wasn't plugged correctly i'm sorry for the time :P

---

### Post by aromo2 on 2013-12-11
Glad you found it out.  There was no software reason to not ping one another.

Please edit the title as SOLVED.

---

