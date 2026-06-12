---
title: "Ping www.blabla returns unknown host .... pinging ip works ...."
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by LordTiggy on 2008-12-01
Hi,

I am pretty new to ubuntu and I had everything running fine until a couple of weeks ago I always get host unknown when pinging a hostname ... even remote connecting to mysql host needed to be changed to ip to make it work.

I looked on many posts here and using google but didn't find anything that could help me ...

I connect using wireless network

ifconfig output:

> 
tiggy@gecko:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:b6:5d:82:ad
          inet addr:10.0.0.250  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:59058 (57.6 KB)  TX bytes:56432 (55.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-B6-5D-82-AD-00-00-00-00-00-00-00-00-00
-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


resolv.conf output:

> 
tiggy@gecko:~$ cat /etc/resolv.conf
search lan
nameserver 193.109.184.66
nameserver 193.109.184.81
nameserver 10.0.0.138


route -n output:

> 
tiggy@gecko:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         10.0.0.138      0.0.0.0         UG    100    0        0 wlan0


and the dhcp.conf (/etc/dhcp3/dhclient.conf)

> 
request subnet-mask, broadcast-address, time-offset, routers, domain-name,    domain-name-servers, host-name, ntp-servers;
prepend domain-name-servers 193.109.184.66,193.109.184.81;


10.0.0.138 is the ip of my router ... on my vista i can ping hostnames fine so it must be some setting on my ubuntu server :|; all pc's use dhcp.

Any ideas what might be wrong? Can some program interfer and give probs? Any help would be nice :)

Greetz and I hope I can solve this with you guys help :)

---

### Post by Iowan on 2008-12-01
Does your router have DNS servers configured?

---

