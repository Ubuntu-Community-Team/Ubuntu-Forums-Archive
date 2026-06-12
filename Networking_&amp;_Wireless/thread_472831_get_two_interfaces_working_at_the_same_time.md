---
title: "get two interfaces working at the same time"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by glenmo on 2007-06-13
how can i get both my interfaces working at the same time?

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:70:2A:32:CD  
          inet addr:192.168.0.235  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:224469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:233075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30080796 (28.6 MiB)  TX bytes:141876417 (135.3 MiB)
          Base address:0x9000 Memory:e5000000-e5020000 

eth1      Link encap:Ethernet  HWaddr 00:50:70:23:32:E8  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1396709 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1469122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:136741391 (130.4 MiB)  TX bytes:975540577 (930.3 MiB)
          Interrupt:17 Base address:0x8000 

eth1:avah Link encap:Ethernet  HWaddr 00:50:70:23:32:E8  
          inet addr:169.254.6.234  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:638307 (623.3 KiB)  TX bytes:638307 (623.3 KiB)


then if i enable eth1 using the network manager applet:

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:70:2A:32:CD  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:225417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30430685 (29.0 MiB)  TX bytes:142016377 (135.4 MiB)
          Base address:0x9000 Memory:e5000000-e5020000 

eth1      Link encap:Ethernet  HWaddr 00:50:70:23:32:E8  
          inet addr:192.168.0.242  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1396899 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1469125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:136765250 (130.4 MiB)  TX bytes:975541321 (930.3 MiB)
          Interrupt:17 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:50:70:2A:32:CD  
          inet addr:169.254.6.120  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Base address:0x9000 Memory:e5000000-e5020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5622 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:639411 (624.4 KiB)  TX bytes:639411 (624.4 KiB)

i want them to both run at the same time -- but the network manager only allows me to choose one... this seems ridiculous to me -- why isn't it a checkbox instead of a radio button and why can't i get this to work?

---

### Post by glenmo on 2007-06-13
no one knows how to do this, huh?  i'll bump it and see if some fresh eyes can see the post.

---

### Post by glenmo on 2007-06-14
i'm on feisty... 



bump...

---

### Post by glenmo on 2007-06-19
this is ridiculous... no one knows how to do this?



NO ONE?


bump.

---

### Post by Mr. C. on 2007-06-19
Define: "working".

MrC

---

### Post by netztier on 2007-06-19
> **glenmo said:**
> this is ridiculous... no one knows how to do this?



NO ONE?


bump.

geez. 

Another one who seems unable to find (or make good use of) the forum's search function.

In this very "Networking & wireless" Subforum, go to the "Search this Forum" menu right atop the post list on the right-hand side of your screen. In the drop-down box, enter *multiple interfaces* as keywords, and then watch what happens: Already on the first page of search results, I can spot half a dozen threads on the topic of running and configuring multiple interfaces.

[COLOR="Red"]CAUTION: you'll have to do a bit of reading! You know, find configuration file excerpts, read other people's problem descriptions and see if their problems are similar to yours and stuff like that[/COLOR]

[COLOR="Red"]**EXPLICIT WARNING: You might actually learn something and increase your knowlodge about (Ubuntu) Linux.**[/COLOR]

Calling something "ridiculous" (with a problem description that lacks detail by a square mile) falls right back on you. You seem to express that you just wish someone else solved your problem which you have failed to describe in an understandable way. The attitude you have shown in your posting style and the bumps might actually be a reason (and a good one at that!) why nobody bothered to answer. 

What is it that you actually want to achieve? Multiple interfaces in different IP networks, to use the system as a router? multiple Interfaces as a "team", having only one IP address in a single IP network? I can guess what you mean - but I refuse to base my answer on assumptions. Give good input, get decent output. Shouting "hey I want this thingything done somehow" is not considered good input.

regards

Marc

---

