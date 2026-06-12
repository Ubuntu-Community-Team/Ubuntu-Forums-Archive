---
title: "network connection"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by flameboy1974 on 2008-02-26
First I must let you know I am very new to Linux. I tried mandrake many years ago and I tried mandriva recently but it had too much crap installed.
So now I found Ubuntu, so far I like it. My wireless works great (unlike in mandriva), but my wired is not working. I use a static Ip address. I used the network config to add the ip address, gateway, DNS servers, ect. I even disabled the wireless just in case. But i can't seem to access the internet. 
I have two little computer showing the connection, I also checked the status and seem butes where being sent and received.
So now I'm not sure what to do. Like I said I very new to linux but seem to be able to find my way around it. I'm most likely overlooked something, so if anyone can save me...please....please help!

---

### Post by flameboy1974 on 2008-02-26
as an update. I am able to ping the router. I just can't figure out why i can't access internet. I just keep getting server not found. Do i have to make Ubuntu use the wired connection somehow? Any help would be great. if there is something that I need to do and post more info just tell me what I need to do. TY.

---

### Post by flameboy1974 on 2008-02-26
ferby@ferby-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:24:9B:7D:1F  
          inet addr:192.168.1.26  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe9b:7d1f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6737174 (6.4 MB)  TX bytes:30928 (30.2 KB)
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94476 (92.2 KB)  TX bytes:94476 (92.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:E8:8B:A8:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-8B-A8-83-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ferby@ferby-laptop:~$

---

### Post by SpaceTeddy on 2008-02-26
can you please post the output of the following comands

> route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
ping -c 4 209.85.135.103
ping -c 4 [www.google.de](www.google.de)


---

