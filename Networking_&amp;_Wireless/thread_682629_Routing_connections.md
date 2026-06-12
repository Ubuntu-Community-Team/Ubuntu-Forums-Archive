---
title: "Routing connections"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by yonthan on 2008-01-30
Hey guys

Im new to Ubuntu, im trying to do something very specific, I have 2 internet connections, and all i want to do it add a gateway so that the one works normally and the other is inactive, then i want to route the other connection to this IP: 196.12.241.242.

I did try sudo route add default gateway 41.241.192.1, but that changes the 0.0.0.0 destination gateway, which leaves both connections not working.

ppp0, 41.241.215.204, 41.241.192.1 is the connection i want to have work normally
ppp1, 172.24.67.170, 10.6.6.6 is the connection i want to route

the following is when i type route -n and ifconfig when both are connected

**route -n:**

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
41.241.192.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
10.6.6.6        0.0.0.0         255.255.255.255 UH    0      0        0 ppp1
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp1
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

**ifconfig:**

eth0      Link encap:Ethernet  HWaddr 00:16:E6:5D:B7:BE  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e6ff:fe5d:b7be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8277 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6394692 (6.0 MB)  TX bytes:1174385 (1.1 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:41.241.215.204  P-t-P:41.241.192.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:892962 (872.0 KB)  TX bytes:133656 (130.5 KB)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:172.24.67.170  P-t-P:10.6.6.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:64 (64.0 b)  TX bytes:97 (97.0 b)

---

### Post by Yhetti on 2008-01-30
I'm kind of unclear on what you're trying to do.  Are you trying to route to a different gateway based on source address?

I'm not sure what you mean by "then i want to route the other connection to this IP: 196.12.241.242."

---

### Post by yonthan on 2008-01-30
The second connection that is inactive because of the gateways needs to be routed to a proxy server.

Iv been looking around, people are saying i should use iptables, i dont even know what they are :s

I did all of this in windows, and it was fairly simple, i just dont know the right commands now

Thanks for the reply

---

### Post by Yhetti on 2008-01-30
> **yonthan said:**
> The second connection that is inactive because of the gateways needs to be routed to a proxy server.

Iv been looking around, people are saying i should use iptables, i dont even know what they are :s

I did all of this in windows, and it was fairly simple, i just dont know the right commands now

Thanks for the reply

Then start by telling us what you did in Windows and we'll try to translate it : )

I'm confused because proxy servers operate at a higher level (layer 7) than routing.  Proxy servers (like squid or SOCKS) are unrelated to routing in the strictest sense.

---

### Post by yonthan on 2008-01-30
OK, well in windows all i did was first connect the usb modem then connect the adsl, therefore the adsl would work and the usb modem would be inactive. then i would go to command prompt and type ipconfig which would give me both the usb and adsl ip address and gateway, i would use the usb ip and say route add <usb ip> <proxy server ip> after that i would be able to use my adsl for everything except flashget (a download manager), i would make flashget download from the proxy only.

---

### Post by Yhetti on 2008-01-30
> **yonthan said:**
> OK, well in windows all i did was first connect the usb modem then connect the adsl, therefore the adsl would work and the usb modem would be inactive. then i would go to command prompt and type ipconfig which would give me both the usb and adsl ip address and gateway, i would use the usb ip and say route add <usb ip> <proxy server ip> after that i would be able to use my adsl for everything except flashget (a download manager), i would make flashget download from the proxy only.

Okay, first off, we have some term confusion.  In this case, what you're talking about isn't a proxy server, it's a gateway.  Secondly, the commandline as you've printed it, in Windows, wouldn't do anything.  The format is

route add <destination> <gateway>

Or, "route any packets bound for my USB modem through the gateway" (which is on the internet).  Clearly, that doesn't make any sense.  I'm surprised it worked at all; it was probably just ignored, since a Metric 0 route (physically attached interface) would always have preference over an added route.  In that case, you could simply choose the correct source address and it would work like you said.  *Technically*, if you just choose the correct source address in Linux, it will work without routing table modifications as well (the routing table is aware that packets that originate from a given source address have to be sent out that interface).

However, it sounds like what you want to do is have your heavy bandwidth applications use one line, and have your interactive traffic use another, automatically?  There's a few different ways to do that.  Linux has a bunch of ways built in to throttle traffic; you don't really have the same limitation in Linux as you do in Windows.  The feature you're looking for is called "source based routing".  That is, the kernel makes the decision on how to route the packet based on the origination address of it (as opposed to the destination address).  

Here's a good example:

[http://answers.google.com/answers/threadview?id=274082](http://answers.google.com/answers/threadview?id=274082)


Some more google searches for "linux policy based routing" might help.  Of course, this is probably way more complicated than you need to make it; the easy answer is to set up your downloader client correctly (or use one of the dozens or web-downloaders instead of Flashgot, may of which are totally automated).  

Or, I might be completely misunderstanding you still : )

---

### Post by yonthan on 2008-01-30
Thanks for replying

yes, you are right, it was route add <proxy ip> <usb gateway>, havent done it for a while, at the end just got a program to do it for me :P

I think there might be a misunderstanding, i basically forced flashget to download from the proxy, I couldnt actually download through my adsl in flashget, I just want to find the equivilant of the windows command: route add <proxy ip> <usb gateway> and be able to have my adsl working perfectly while the usb modem is connected

I using running Flashget through Wine,

---

