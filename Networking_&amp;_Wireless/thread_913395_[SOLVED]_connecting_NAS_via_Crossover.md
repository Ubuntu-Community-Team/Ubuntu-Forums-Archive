---
title: "[SOLVED] connecting NAS via Crossover"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by MunkyJunky on 2008-09-07
I was bought an Acer Aspire easystore network attatched storage a while back, and have been using it happily through my router. But now, I'm moving away to go to university, and having your own routers on the uni network is a big no-no. However, I can't get it connecting when plugged directly into my comp, using a crossover cable. 

I have two network connections, eth0 for my NAS, and eth1 for my LAN (and www access). I tried configuring the NAS as a DHCP server - no luck. configuring eth0 and the NAS with static IP's had no luck either. 

A friend of mine is pretty well versed in linux, and helped me try a few things, non of which worked either. Ping shows 'host unreachable', traceroute times out, and the ouput of route is: 

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.10.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         mygateway1.ar7  0.0.0.0         UG    100    0        0 eth1

```

Anyone have ANY idea on what I can do to try figure this out?

---

### Post by bab1 on 2008-09-07
Do you know the IP address of the NAS?  Why do you feel you need to use a router to connect to the NAS? Are you restricted to one port (MAC filtering)?  

Some consumer routers routers (like Linksys) allow you to spoof the MAC address and run an entire multihost network behind it.  You could then hook up the NAS with a simple switch.

---

### Post by MunkyJunky on 2008-09-08
I can set the IP of the NAS to anything I want through the NAS web admin page. I'm currently connecting to the NAS through a router, since its convinient for me. However, in 2 weeks I move into university accomodation and don't want to have to buy a switch or router - I just want to connect directly to the NAS via a crossover cable.

I'm not restricted to one port, there's no sort of MAC filtering either. I just don't want to buy a switch or router when I have a crossover cable I could use.

---

