---
title: "Network reverts to loopback interface (lo) on reboot"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by Gnusboy on 2014-02-01
Ubuntu 12.04

Problem #1 -
My system and network frequently run very slow offline or online while browsing. I have older but fairly powerful hardware, hardwired to a DSL modem at 5 to 7 mb but lately it has been very slow to connect on several sites that don't get much traffic. It is also sporadic in the connections. One time it will hang until I disconnect, yet a different attempt will make the connection quickly. 
I checked the network devices and it is set to loopback interface (lo).
The IP information setting is 
Protocol -  IPv6 ::1 
Netmask  - 128
Scope - host

It was originally set at (eth0) but sometime ago I changed it to loopback interface (lo) thinking that the change would help my browsing faster. It still stayed slow and began to be even slower. [SIZE=5]When it continued to run slow, I looked up the network  settings and saw that the loopback interface could be the problem  slowing everything down.
I changed the device setting to ethO 
The IP information shows 
"Ipv6 setting "fe80::224:8cff:fe33:e135:  64"  
"IPv4 setting of 192.168.0.3" is underneath that."

The problem is that after a system reboot, the network automatically returns to the loopback (lo) config. 

Can someone help me figure out which setting I should use and how to config it? 
The hangs and errors are crazy making.
----------------------------------------------------------
Problem #2 - 

Under both settings,I  tried to ping my provider, [www.centurylink.com](www.centurylink.com) and after a long slow wait this message came up:
In either eth0 or loopback I get the same error message:
An error occurred when tried to run ping[/B]
/bin/ping ping -b -c 5 -n [www.centurylink.com](www.centurylink.com)

I pinged a few other sites and sometimes they seemed OK, but other times they were slow..
 
What does this mean? How do I fix it?

I want to figure these problems out soon so I can upgrade to a newer Ubuntu version.

]Thanks for your help.

---

### Post by praseodym on 2014-02-01
Please show:

```
uname -a
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/NetworkManager.conf 
```

---

### Post by Gnusboy on 2014-02-02
Thanks. I'll give it a try.

---

