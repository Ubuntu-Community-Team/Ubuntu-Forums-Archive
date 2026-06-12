---
title: "wlan and pppoe"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by rossmoore on 2008-09-22
Hi,
I have a problem with using pppoe over wlan.

My laptop has built-in wireless which works fine in ubuntu. I have a belkin wireless router (which also has a built-in adsl modem) - of which I am the administrator. I also have, from my broadband company (PCCW in Hong Kong), a wired router and adsl modem. I don't have much access to this box. This box also supplies TV over the broadband connection to another box (which connects via an ethernet cable).

If I plug my laptop into the PCCW router by ethernet cable I can run pppoeconf, fill in my details and away we go. Broadband connection works perfectly. For info, here's the output from route and ifconfig:
```
:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
pcd-lkt9-1-rx.n *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0
default         *               0.0.0.0         U     1000   0        0 eth0
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:4c:4b:2e  
          inet6 addr: fe80::21d:9ff:fe4c:4b2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172069 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:162478085 (154.9 MB)  TX bytes:32444427 (30.9 MB)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:09:4c:4b:2e  
          inet addr:169.254.3.38  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:177626 (173.4 KB)  TX bytes:177626 (173.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:58.153.102.93  P-t-P:219.78.200.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:158246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:160576142 (153.1 MB)  TX bytes:27000707 (25.7 MB)

```

Now, I don't understand the output from route - what is the destination "pcd-lkt9-1-rx.n" meant to mean?

I can now unplug the ethernet cable from my laptop, plug it into my wireless router (one of its 4 ethernet sockets), and then hook up my wireless on the laptop to the wireless router over wlan. I then run pppoeconf again, and everything seems to go fine, except now the output from route looks like this:
```
:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
219.78.200.254 *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     0      0        0 wlan0
default         *               0.0.0.0         U     0      0        0 ppp0
default         *               0.0.0.0         U     1000   0        0 wlan0
```

Note the desination in the top line is now the pppoe ip address listed in ifconfig. And now I can't browse the net, or ping anything (by ip address or by domain name so it's not a DNS issue).

I feel the key is to understand what those characters in the routing table are doing there, but apart from that I'm stumped.

Any ideas greatly appreciated!
Thanks,
Ross

---

### Post by rossmoore on 2008-10-06
bump!
Does anyone have any ideas on what to do next?

Are there any networking gurus out there?

---

### Post by rossmoore on 2008-10-13
I really intrigued to find out what the results of route (quoted above) mean.

Why would internet connectivity work when the destination is that random set of letters, but not when an IP address is reported?

---

