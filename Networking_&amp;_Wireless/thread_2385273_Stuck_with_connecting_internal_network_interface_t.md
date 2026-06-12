---
title: "Stuck with connecting internal network interface to external network interface"
date: 2018-02-18
forum: Networking &amp; Wireless
---

### Post by abdulsattar86 on 2018-02-18
I am on Ubuntu 16.04.  My system has two network interfaces enp0s3 which is connected to my wireless network and enp0s8 which is connected to my internal network. 

I want hosts on my internal network to be able to talk to external network (internet) through my system. 

On my host when I do 

ping 192.168.0.29  //ip address of enp0s3 interface on my host

I get a response which is fine

However when I do 

ping -I enp0s8 192.168.0.29

the ping packets are lost. Also doing tcpdump on enp0s3 interface for icmp packets does not show any activity

I have also enabled ip forwarding and have the following ip table rules

[COLOR=#000000][FONT=Consolas]FORWARD -i enp0s3 -o enp0s8 -m state --state RELATED,ESTABLISHED -j ACCEPT
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]FORWARD -i eth0 -o eth1 -j ACCEPT
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]POSTROUTING -o enp0s8 -j MASQUERADE
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]

Please help! Why does this have to be so hard??? I am stuck on it for a couple of days now!
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]


[/FONT][/COLOR]

---

