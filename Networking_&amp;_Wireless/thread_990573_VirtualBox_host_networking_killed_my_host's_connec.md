---
title: "VirtualBox host networking killed my host's connectivity"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by ubernatural on 2008-11-22
Hi,

I'm a bit confused.  I followed the instructions in the VirtualBox manual to set up a permanent bridge connection for host networking in a Vista guest.  This worked perfectly.  Now, unfortunately I've lost Internet in the host (Intrepid).  Network manager shows now TWO entries for Auto eth0 (both selected) where there previously was only one.  Here's my ifconfig output:

```
br0       Link encap:Ethernet  HWaddr 00:1b:fc:1c:e7:92  
          inet addr:192.168.21.101  Bcast:192.168.21.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:326598 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2744151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51987747 (51.9 MB)  TX bytes:3747364174 (3.7 GB)

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:1c:e7:92  
          inet addr:192.168.21.101  Bcast:192.168.21.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:147189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171595 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:130884251 (130.8 MB)  TX bytes:116163851 (116.1 MB)
          Interrupt:254 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:598 errors:0 dropped:0 overruns:0 frame:0
          TX packets:598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46466 (46.4 KB)  TX bytes:46466 (46.4 KB)

vbox0     Link encap:Ethernet  HWaddr 5a:c4:b4:9f:ba:22  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:283453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2732869 errors:0 dropped:1733 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:25223353 (25.2 MB)  TX bytes:3752395581 (3.7 GB)
```

I get no Internet on the host, no ping responses - though I can see the guest machine and DNS also does work.  Am I missing something really basic here?

EDIT: I failed to mention that Internet / networking works great in the guest.  In fact, that's where I am now...

---

### Post by SpideySpirit on 2008-11-24
:lolflag: Glad I'm not alone with this problem, uber if it helps I have a thread going to address this issue.... unfortunately not solved...:confused:
[**_"No Internet. But my VBox XP guest is OK?"_**]("http://ubuntuforums.org/showthread.php?t=986788")

---

### Post by ubernatural on 2008-11-25
I've mostly (well, to my satisfaction) resolved my issue.  Details in SpideySpirit's post (linked above).

---

