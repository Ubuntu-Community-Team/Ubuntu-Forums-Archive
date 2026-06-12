---
title: "ubuntu to xubuntu wifi sharing"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by Dekadence on 2008-01-12
Hi!

I need a little help with setting my wireless connection between Ubuntu desktop and xubuntu laptop (asus eee 701). I have ethernet cable plugged in desktop form router and configured with DHCP. Desktop has also wifi card, and I'd like to share internet with laptop trough wifi. I've done those things with Firestarter and all and laptop detects desktop and I can also connect to it trough wifi-radar, but internet still doesn't work! I don't know what is the problem but I suspect those IP and gateway numbers. Here's my current situation:

ifconfig on Desktop:

```

eth0      Link encap:Ethernet  HWaddr 00:18:F3:08:86:8B  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe08:868b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37792822 (36.0 MB)  TX bytes:3074602 (2.9 MB)
          Interrupt:17 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5421 (5.2 KB)  TX bytes:5421 (5.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:4D:EF:0B:10  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Memory:feae0000-feaf0000 


```


Laptop ifconfig:

```

ath0      Link encap:Ethernet  HWaddr 00:15:AF:45:CC:45  
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe45:cc45/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:1E:8C:0A:3B:A3  
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe0a:3ba3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149 errors:0 dropped:0 overruns:0 carrier:11
          collisions:0 txqueuelen:1000 
          RX bytes:66214 (64.6 KB)  TX bytes:0 (0.0 b)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13844 (13.5 KB)  TX bytes:13844 (13.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-AF-45-CC-45-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22746 errors:0 dropped:0 overruns:0 frame:1223
          TX packets:22176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1409255 (1.3 MB)  TX bytes:1092763 (1.0 MB)
          Interrupt:18 

```

It'd be nice if someone could tell me how to configure this! And please, I want to keep that connection with router the way it is now (IP of desktop: 192.168.1.64 and so on...) Thanks!

---

### Post by snek on 2008-01-13
I have been looking into this exact same setup. At the moment I just have my laptop plugged into router with a cable, but dragging that cable around is getting annoying ;)

My ubuntu server has a prism2 card, but is also hooked up to the router via a gbit nic. I know it is near impossible to make this setup under Windows so I thought it might have been a "logic problem" where it is just impossible to setup something like this.

My first problem was that after having setup wlan0 my internet connection on eth0 died. There used to be an option somewhere to set the "default connection" but I can't find that anymore.

There must be someone with a working setup like this?

---

### Post by Dekadence on 2008-01-13
> **snek said:**
> My first problem was that after having setup wlan0 my internet connection on eth0 died. There used to be an option somewhere to set the "default connection" but I can't find that anymore.

Yes, that happened to me sometimes too! I'm really looking forward to the solution of this problem because I know (think?) it's possible!

---

### Post by Dekadence on 2008-01-14
bump?

---

