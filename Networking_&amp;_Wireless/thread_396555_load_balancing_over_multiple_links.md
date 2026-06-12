---
title: "load balancing over multiple links"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by sefmars on 2007-03-29
has anyone done load-balancing over multiple links in ubuntu/kubuntu??

i have a scenario like this :

2 internet connections :
eth0 xxx.xxx.xxx.xxx
eth1 xxx.xxx.xxx.xx

eth0 and eth1 have the same broadcast domain and same default gateway,they are in the same network, 

2 other network cards bridged forming br0 10.10.0.1/24


so i need nat, ttl increase, and load-balancing over multiple links


has anyone tried theat ??

seen this :

[http://tetro.net/misc/multilink.html](http://tetro.net/misc/multilink.html)


and this

[http://lartc.org/howto/lartc.loadshare.html](http://lartc.org/howto/lartc.loadshare.html)

and this 

[http://www.linux.com.lb/wiki/index.pl?node=Load%20Balancing%20Across%20Multiple%20Links](http://www.linux.com.lb/wiki/index.pl?node=Load%20Balancing%20Across%20Multiple%20Links)

and this

[http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)

none seems to be a solution

looking forward to solve the problem

---

### Post by koenn on 2007-03-29
I haven't done this before, but had a quick look at the 4 links you show, and all 4 seem to offer a working sollution, and quite doable. 

why exactly do you think that "none seems to be a solution" ?

---

### Post by Mr. C. on 2007-03-29
What level are you trying to load balance ?  What are you trying to accomplish?  Load-balancing is a broad term, so you'll have to define your goals a bit better.

MrC

---

### Post by sefmars on 2007-04-05
mainly i need redundancy and an equal distribution of the traffic

---

### Post by sefmars on 2007-04-13
i found this that looks kind of intresting I'll try it this week and see how it goes, hope it works and doesn't affect any service that I'm running

[http://www.debian-administration.org/articles/377](http://www.debian-administration.org/articles/377)

---

