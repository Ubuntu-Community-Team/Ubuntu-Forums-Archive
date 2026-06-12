---
title: "edgy -- two NICS"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by georgeh on 2007-03-01
Hello everyone,
I have an ubuntu edgy setup with the latest updates..
I have two NICS on the machine, one with a 192.168.0.x IP and the other NIC with a 137.79.65.X IP. Initially the setup works, meaning I can surf the web and I can ping the 192.168.0.x of IPs, but once I reboot, i can no longer go online untill i disable one of the interfaces. Can anyone help me out with this issue?

---

### Post by tdhombre on 2007-03-01
Configure them as separate interfaces by using the /etc/iftab mechanism.  You define the different names and with their unique mac addresses (use "ifconfig" to determine the mac addresses) to force them to be consistent and different names.  Then configure each name appropriately in /etc/network/interfaces.  Refer to the man pages for more detailed information.   

:lolflag:

---

### Post by georgeh on 2007-03-02
I tried what you said and once i enable the interface, internet stops working..
here is a copy of /etc/iftab & /etc/network/interfaces
```


cat /etc/iftab 
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:19:b9:05:ff:aa arp 1

eth1 mac 00:0e:0c:76:b5:04 arp 1



```
copy of ifconfig output
```

eth0      Link encap:Ethernet  HWaddr 00:19:B9:05:FF:AA  
          inet addr:137.79.65.61  Bcast:137.79.65.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe05:ffaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1223353 (1.1 MiB)  TX bytes:262632 (256.4 KiB)
          Interrupt:169 

eth1      Link encap:Ethernet  HWaddr 00:0E:0C:76:B5:04  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:782 (782.0 b)  TX bytes:3847 (3.7 KiB)

```
```
 
cat /etc/network/interfaces 
auto lo
iface lo inet loopback


#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp









iface eth0 inet static
address 137.79.65.61
netmask 255.255.255.0
gateway 137.79.65.1
network 137.79.65.0
broadcast 137.79.65.255
auto eth0

iface eth1 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
network 192.168.0.0
broadcast 192.168.0.255
auto eth1


```

---

### Post by georgeh on 2007-03-03
Does anyone have a clue as to why this might happening?

---

### Post by pr0f1t on 2007-03-04
I am having the same issue. Did you ever find a solution to this? I see none was ever posted here.

---

### Post by netztier on 2007-03-05
> ```
 ...
iface eth0 inet static
address 137.79.65.61
netmask 255.255.255.0
[COLOR="Red"]gateway 137.79.65.1[/COLOR]
network 137.79.65.0
broadcast 137.79.65.255
auto eth0

iface eth1 inet static
address 192.168.0.3
netmask 255.255.255.0
[COLOR="Red"]gateway 192.168.0.1[/COLOR]
network 192.168.0.0
broadcast 192.168.0.255
auto eth1
```

Normally, you can have only **one** active default route in your internal routing table. Check it's content with **netstat -nr**. First default route (0.0.0.0, mask 0.0.0.0) will be active one.

Conclusion: One of the entries marked above has to go. Most probably it will be the one for "gateway 192.168.0.1", since most of the time, the default route points towards the Internet. If there are other IP networks connected to routers on the subnet of eth1, you'll have to add specific static routes for them.

best regards

Marc

---

### Post by georgeh on 2007-03-06
> **netztier said:**
> Normally, you can have only **one** active default route in your internal routing table. Check it's content with **netstat -nr**. First default route (0.0.0.0, mask 0.0.0.0) will be active one.

Conclusion: One of the entries marked above has to go. Most probably it will be the one for "gateway 192.168.0.1", since most of the time, the default route points towards the Internet. If there are other IP networks connected to routers on the subnet of eth1, you'll have to add specific static routes for them.

best regards

Marc
Hey Marc,
I am hitting two different routers on different network cards.. how would i add the second router then (192.168.0.1)? if i don't include it in the /etc/network/interfaces?

---

### Post by Mr. C. on 2007-03-06
You are misunderstanding - your system must make a decision.

It KNOWS how to send to the 192.168.0/24 network - its directly connected to it.

It KNOWS how to send to the 137.79.65.1/24 network - its directly connected to it.

Gateway means, for all those networks it DOESN'T know about, where it should send the traffic.

Your system can't send out to two different gateways; you must select one.  Select the one attached to your broadband connection.  Its address will be the default gateway.

MrC

---

### Post by georgeh on 2007-03-06
> **Mr. C. said:**
> You are misunderstanding - your system must make a decision.

It KNOWS how to send to the 192.168.0/24 network - its directly connected to it.

It KNOWS how to send to the 137.79.65.1/24 network - its directly connected to it.

Gateway means, for all those networks it DOESN'T know about, where it should send the traffic.

Your system can't send out to two different gateways; you must select one.  Select the one attached to your broadband connection.  Its address will be the default gateway.

MrC

Hmm..ok. so i know it is directly connected to that network. I know that my computer can ping, access networkr esources on the 137.79.65.1 network.. now about the second interface, I want to be able to access resources on the 192.168. network, if i doesn't know how to get here, how can i access shares there? I am assuming by the previous poster that i need to add to the routing table. Ok, so then, how do i  go about modify ing the routing table and make it permanent? and thank you for your help.

---

### Post by Mr. C. on 2007-03-06
Let see what you have first:

netstat -r

MrC

---

### Post by netztier on 2007-03-07
> **georgeh said:**
> Hey Marc,
I am hitting two different routers on different network cards.. how would i add the second router then (192.168.0.1)? if i don't include it in the /etc/network/interfaces?

Ah.. so we need one default route (towards the internet) with the ISP's router as next hop. There can only ever be one active default route. In a routing table, it's first "best match"  (also called "longest match" or "most specific") and secondly "first in table".

So if a given destination IP address doesn't match any of the specific entries present in the table, it matches the (first) default route and is sent to that route's "next hop" address.

Now if you have other 192.168.x.* subnets you want to reach via the router on 192.168.0.1, you cannot do this with another *default route*, but you have to add **static routes**. They will appear in the routing table and will lead to a "more specific" match than the default route and thus take precedence.

This can be done with the **route** command. Example: Network 192.168.100.0 /24 is reachable via the router 192.168.0.1 . You'd then add this static route:

```
sudo **route add -net 192.168.100.0 netmask 255.255.255.0 gw 192.168.0.1**
```

I'm currently trying to figure out how to make this stick, so the route is back when the system reboots...

To understand your actual case I'd concur with MrC: show us your current routing table (**route** or **netstat -nr**), and we'll see what we can do.

best regards

Marc

---

### Post by Mr. C. on 2007-03-07
Static Routes: [http://www.ubuntuforums.org/showthread.php?t=113474&highlight=static+routing](http://www.ubuntuforums.org/showthread.php?t=113474&highlight=static+routing)

If you want to learn about routing, see Week 6 Notes and Labs.

[http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

MrC

---

### Post by netztier on 2007-03-07
> **Mr. C. said:**
> Static Routes: [http://www.ubuntuforums.org/showthread.php?t=113474&highlight=static+routing](http://www.ubuntuforums.org/showthread.php?t=113474&highlight=static+routing)


Ok, that does the job in the "good" way: call an external shell script that adds or removes routes (or does other things) with the interface going up or down. And with flushing the table befor adding new routes, things are of course well-set up and well-defined. I'd call that the *cleaner* approach.

If however it's just a "one-liner" that's needed, going *quick & dirty *might also be good enough:

```
**/etc/network/interfaces**[FONT="Courier New"]
 ...
auto eth1
 ...
iface eth0 inet static
 address 192.168.0.3
 netmask 255.255.255.0
 broadcast 192.168.0.255
[COLOR="Green"] up route add -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.0.1
 down route del -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.0.1[/COLOR] 
 ...[/FONT]
```

I found this in [Configure static routes in Debian or Red Hat Linux systems]("http://www.cyberciti.biz/tips/configuring-static-routes-in-debian-or-red-hat-linux-systems.html#deb") and adapted it to the configuration in the OP's /etc/network/interfaces. It assumes that *any*192.168.*.* network is reachable via the next hop router 192.168.0.1

Make sure to check the routing table's contents afterwards!

best regards

Marc

---

### Post by georgeh on 2007-03-08
netstat -nr
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
137.79.65.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.0.0     192.168.0.1     255.255.0.0     UG        0 0          0 eth1
0.0.0.0         137.79.65.1     0.0.0.0         UG        0 0          0 eth0

```
it's seems to be working! thank you guys, I appreciate it all the help.

---

### Post by Mr. C. on 2007-03-08
That's great news - nice work!

Netztier (Mark): no one-upping you intended.  I think we posted or started posting near the same time.

MrC

---

