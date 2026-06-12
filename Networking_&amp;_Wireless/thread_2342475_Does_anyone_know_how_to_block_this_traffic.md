---
title: "Does anyone know how to block this traffic?"
date: 2016-11-07
forum: Networking &amp; Wireless
---

### Post by buntuluxx on 2016-11-07
Hi!

I have been trying to disable this functionality for quite some time, but cannot seem to figure it out.

Within a 1 minute interval several packet sniffer tools report constant traffic from all-systems.mcast.net with a set size of 14 bytes. 
[http://s9.postimg.org/kacufgcbj/screen2.png](http://s9.postimg.org/kacufgcbj/screen2.png)
.

```
ubuntu@ubuntu:~$ netstat -g
IPv6/IPv4 Group Assignments
interface   RefZäh Group
--------------- ------ ---------------------
lo              1      all-systems.mcast.net
eth0            1      all-systems.mcast.net
lo              1      ip6-allnodes
lo              1      ff01::1
eth0            1      ff02::1:ff84:d990
eth0            1      ip6-allnodes
eth0            1      ff01::1

```

Its designated IP is 224.0.0.1
```
ubuntu@ubuntu:~$ netstat -ng
IPv6/IPv4 Group Assignments
interface   RefZäh Group
--------------- ------ ---------------------
lo              1      224.0.0.1
eth0            1      224.0.0.1
lo              1      ff02::1
lo              1      ff01::1
eth0            1      ff02::1:ff84:d990
eth0            1      ff02::1
eth0            1      ff01::1



```


I have already managed to stop other multicast packets, namely traffic from 224.0.0.251, using this:

```
sudo ifconfig eth0 -multicast
```

However, this has not stopped the all-systems.mcast.net traffic.

I have also unsuccessfully tried iptables, inspired by a website regarding the opposite of what I am trying to do:
[https://www.centos.org/forums/viewtopic.php?t=8286](https://www.centos.org/forums/viewtopic.php?t=8286)

```

sudo iptables -A INPUT -s 224.0.0.0/4 -j REJECT
sudo iptables -A INPUT -d 224.0.0.0/4 -j REJECT
sudo iptables -A INPUT -s 240.0.0.0/5 -j REJECT
sudo iptables -A INPUT -m pkttype --pkt-type multicast -j REJECT
sudo iptables -A INPUT -m pkttype --pkt-type broadcast -j REJECT
```


Does anyone know how to stop this 224.0.0.1 / all-systems.mcast.net traffic?

Thanks

---

### Post by gordintoronto on 2016-11-07
Are you running a DLNA server?

[https://davidsimpson.me/2015/11/16/why-is-my-machine-contacting-all-systems-mcast-net/](https://davidsimpson.me/2015/11/16/why-is-my-machine-contacting-all-systems-mcast-net/)

---

