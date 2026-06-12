---
title: "ALL network traffic directed through Hamachi?"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by LaserCobra on 2008-03-18
I want to ensure all internet or network traffic for that matter, goes through my Hamachi virtual interface. I can connect and setup Firefox to use my Hamachi connection for browsing but I'd like to take that a step further. Is that possible? Seemingly like 75% of Ubuntu users, I'm new to Linux so go easy on me.

Thanks!

---

### Post by nixscripter on 2008-03-19
One way to set up which interface traffic goes out on is with the routing table in the kernel. If the virtual interface is a network interface, this would be fairly simple. To see if it is, go to a terminal and type: ```
ifconfig -a
``` and post the output.

---

### Post by LaserCobra on 2008-03-19
Thank you for offering to help. I was thinking a simple route would do the trick but I'm not a power user so tread lightly in Linux. I already killed my install once. Here are the results with Hamachi running:

```
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:6B:5D:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:A9:5D:91  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fea9:5d91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1385 errors:1 dropped:1 overruns:0 frame:0
          TX packets:1287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1138210 (1.0 MB)  TX bytes:251864 (245.9 KB)
          Interrupt:20 Base address:0x4000 Memory:e0206000-e0206fff 

ham0      Link encap:Ethernet  HWaddr 00:FF:0D:3E:87:5C  
          inet addr:5.76.254.205  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5248 (5.1 KB)  TX bytes:5248 (5.1 KB)

```

---

### Post by nixscripter on 2008-03-22
Okay, it looks like Hamachi is a virtual interface, and it does have an IP. Just checking. I suspect it is a routing problem, you're right.

The way I know how to address that on Linux is to use the route command. I'd like to see it. To just dump the routing table, use ```
route
``` I expect to see two entries like this:

```

Destination     Gateway    Genmask      Flags Metric Ref    Use Iface
5.0.0.0         *          255.0.0.0    U     0      0      0   ham0
...
default         *          **router-ip**    U     0      0      0   eth1

```

where **router-ip** is on the local network of 192.168.0.0. This indicates that the traffic not going specifically to the 5.0.0.0 network should be sent down the ethernet card (instead of through the virtrual network). If this is the case, changing the default route should solve the problem (I hope): ```
sudo route add default ham0
```

Let me know how that works.

---

### Post by LaserCobra on 2008-03-27
Thank you again for the assistance. I was finally able to attempt the route add today but was unsuccessful. In the process of that and performing more searches, I think I know better how to explain what it is I want to do. It's rather complicated now that I think it through but I'll ask the question anyway:

Laptop connected to a D-Link router whose gateway is 192.168.0.1 (work DSL)
I have a eth1 with an IP of 192.168.0.100 (issued by work DSL router)
I have a ham0 virtual interface of 5.7.49.49 (or something of the sort)
I can proxy all my web traffic through Hamachi to a computer on my home's LAN and send that out via FreeProxy to the web. So I'm surfing as if I were at home.

I want to take that a step further and access resources on my home LAN via Hamachi while remote. An example of what I want to access is my NAS. I have a SMB mount setup on the laptop and I would like to open that mount in a native fashion, not rdesktop into my home system and do it that way.

The NAS IP is 192.168.0.102.

I tried setting up a source/destination route of 192.168.0.102 5.9.25.25 (home computer's Hamachi IP) and it failed. I think that was partially due to the fact that I'm accessing the LAN via another computer. I'm thinking I need to setup another rule via FreeProxy that will route those type of requests to the LAN.

Time to do more searching and get another beer--- reverse that... get another beer and do more searching.

I hope all this made sense. MMMM beer.

---

### Post by archwaypms on 2008-04-17
if you make the default route through hamachi, you will cut off the branch you are sitting on.  Hamachi will lose its connection which is made on the first original default route.

I have been wondering about this as I need to use the remote gateway at the other end to authenticate myself with a swipe card, and I cannot get the far end router to know a route back to me via hamachi...

If you fix this routing idea i would love ot know.

Gerry Bulger

---

