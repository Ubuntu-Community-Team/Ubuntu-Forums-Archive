---
title: "Default gateway in /etc/network/interfaces seems to be ignored"
date: 2014-02-27
forum: Networking &amp; Wireless
---

### Post by Kevin_Walter on 2014-02-27
Hi there i have a problem with my linux virtual machine


**Structure**: 
I am using a dedicated server from "Online.net" with an extra ip address. On the server i have installed esxi 5.1. For the people who want to know what server it is:[http://www.dell.com/fr/entreprise/p/poweredge-r210-2/pd](http://www.dell.com/fr/entreprise/p/poweredge-r210-2/pd) The vm on the esxi server is a clean Ubuntu 12.04 (I just installed it)


**Problem**: 
Every time i restart the server, my network connection is not set correct. I need to do a few extra steps to get it to work. That results in the following: Every time i reboot the server it hangs for like 1:30 minutes because it cannot find the correct network settings.


**Technical**: 
To get pinging to an ip address to work i need to do this: 

```
route add 62.210.123.1 dev eth0
route add default gw 62.210.123.1

```Otherwise it just says: Network is unreachable After that to get it fully functional i need to do this:
```
nano /etc/resolv.conf

```and add: nameserver 8.8.8.8 and after that:
```
service networking restart

```Everything works now.


My /etc/network/interfaces looks like this:
```


auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
     address 212.83.168.209
     netmask 255.255.255.0
     network 212.83.168.0
     broadcast 212.83.168.255
     gateway 62.210.123.1
     dns-nameservers 62.210.16.6 62.210.16.7

```

I really hope someone can help me with this problem.

---

### Post by The Cog on 2014-02-27
I'm not sure I understand your network setup there, but this version of /etc/network/interfaces may help (don't know how you would recover if it breaks things):

```
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
     address 212.83.168.209
     netmask 255.255.255.0
     network 212.83.168.0
     broadcast 212.83.168.255
     gateway 62.210.123.1
     dns-nameservers 62.210.16.6 62.210.16.7 8.8.8.8
     up route add 62.210.123.1 dev eth0
     up route add default gw 62.210.123.1

```

---

