---
title: "Communication between two subnets problem"
date: 2016-09-02
forum: Networking &amp; Wireless
---

### Post by m4dmax on 2016-09-02
[COLOR=#111111][FONT=Ubuntu]I have a simple network described below: [/FONT][/COLOR]
Server1 (Two NICs):  
eth0: xxx.xxx.xxx.xxx Public IP address connected to ISP device  
eth1: 192.168.0.1 LAN1(192.168.0.0)

Server2 (Two NICs):  
eth0: 192.168.0.3   
eth2: 192.168.1.1 LAN2(192.168.1.0)
[COLOR=#111111][FONT=Ubuntu][IMG]http://i.stack.imgur.com/P89Hg.png[/IMG]
What I would like to do is to communicate machines from LAN1 with machines from LAN2.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Below I put the output of **ip addr** and **ip route** of both servers
**Server1**
***ip addr***[/FONT][/COLOR]
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether d4:ae:52:cc:13:69 brd ff:ff:ff:ff:ff:ff
    inet xx.xx.xx.xxx/30 brd xx.xx.xx.xxx scope global eth0
    inet6 fe80::d6ae:52ff:fecc:1369/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether d4:ae:52:cc:13:6a brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.1/24 brd 192.168.0.255 scope global eth1
    inet6 fe80::d6ae:52ff:fecc:136a/64 scope link
       valid_lft forever preferred_lft forever
[COLOR=#111111][FONT=Ubuntu]***ip route***[/FONT][/COLOR]
default via xxx.xxx.xxx.xxx dev eth0  metric 100
yyy.yyy.yyy.yyy/30 dev eth0  proto kernel  scope link  src zzz.zzz.zzz.zzz
192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.1
192.168.1.0/24 via 192.168.0.3 dev eth1
[COLOR=#111111][FONT=Ubuntu]where:
xxx.xxx.xxx.xxx is my ISP Gateway
yyy.yyy.yyy.yyy/30 is my subnet
zzz.zzz.zzz.zzz is my public IP address (but it doesn't matter in this case)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**Server2**
***ip addr***[/FONT][/COLOR]
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:23:54:c0:43:9e brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.3/24 brd 192.168.0.255 scope global eth0
    inet6 fe80::223:54ff:fec0:439e/64 scope link
       valid_lft forever preferred_lft forever
3: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether ec:08:6b:06:3f:dd brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.1/24 brd 192.168.1.255 scope global eth2
    inet6 fe80::ee08:6bff:fe06:3fdd/64 scope link
       valid_lft forever preferred_lft forever
[COLOR=#111111][FONT=Ubuntu]***ip route***[/FONT][/COLOR]
192.168.1.0/24 dev eth2  proto kernel  scope link  src 192.168.1.1
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.3
default via 192.168.0.1 dev eth0  metric 100
[COLOR=#111111][FONT=Ubuntu]Below is the output of traceroute command from **Server1**. Maybe it helps:
traceroute to 192.168.1.14 (192.168.1.14), 30 hops max, 60 byte packets 1  192.168.0.3 (192.168.0.3)  0.102 ms  0.092 ms  0.084 ms 2  * * * 3  * * * 4  * * * 5  * * * 6  * * * 7  *^C

[/FONT][/COLOR]
Has anyone an idea what is wrong here. What should I do to get it work?

I will appreciate any help :)

---

### Post by The Cog on 2016-09-02
Three possible porblems I can think of:

1:
Server2 is not configured to forward IP packets (it's disabled by default):
[http://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent](http://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent)

2:
192.168.1.14 doesn't know that replies to network 192.168.0.x must go via 192.168.1.1.
Use "ip route" on linux or "route print" on windows to inspect the routing table on 192.168.1.14.

3:
A firewall somewhere is blocking things. Could be any of the machines involved.

Nice diagram by the way.

---

### Post by m4dmax on 2016-09-06
Thanks @The Cog.
Suggestion numer 2 solved my problem :)

---

