---
title: "Cannot connect to router after pppoeconf"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by izak on 2008-06-18
Hi

Because I'm using my netgear router in bridge mode I've been using pppoe for some time now. 

However, today I tried to access the router again through its IP address, but I get an error in firefox:
> The following error occurred:
[code=CANT_CONNECT] Could not connect because of networking problems. Contact your system administrator. 

I can connect to websites and the internet, just not to my router's IP (http://192.168.0.1/). 

What should I do? I've tried using  "sudo poff dsl-provider" to stop the pppoe connection but then I can't connect to anything (as expected).

*As an aside: the reason I want to connect to the router is to change the DNS settings to use openDNS for content filtering. Will this work with PPPoE? (i.e. name and password stored on the PC but DNS IP stored on the router)*

---

### Post by izak on 2008-06-18
Has this got somethig to do with it?
```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
41.241.160.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
```

---

### Post by superprash2003 on 2008-06-18
yes DNS stored on router would work.. but in your pc you should point DNS as the router ip.. could you please post your ifconfig output

---

### Post by izak on 2008-06-19
Thanks, I will do this tonight (it is my home PC)

---

### Post by izak on 2008-06-19
Here's the output.

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:f5:cc:cb  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68282 (66.6 KB)  TX bytes:19777 (19.3 KB)
          Interrupt:23 Base address:0x8000 

eth0:avahi Link encap:Ethernet  HWaddr 00:e0:4c:f5:cc:cb  
          inet addr:169.254.11.127  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140100 (136.8 KB)  TX bytes:140100 (136.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:41.244.192.172  P-t-P:41.241.160.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:64189 (62.6 KB)  TX bytes:12287 (11.9 KB)

```

---

### Post by superprash2003 on 2008-06-19
go to system->administration->network and go to eth0 properties and set it to DHCP.. you should now get an ip in eth0.. please post ifconfig again after doing this

---

### Post by izak on 2008-06-20
Thanks for the help. Changed the "wired connection" from "roaming mode" to DHCP. Here is the ifconfig results:
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:f5:cc:cb  
          inet6 addr: fe80::2e0:4cff:fef5:cccb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1989 (1.9 KB)  TX bytes:6498 (6.3 KB)
          Interrupt:23 Base address:0x8000 

eth0:avahi Link encap:Ethernet  HWaddr 00:e0:4c:f5:cc:cb  
          inet addr:169.254.11.127  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2468 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123400 (120.5 KB)  TX bytes:123400 (120.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:41.241.189.54  P-t-P:41.241.160.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:650 (650.0 B)  TX bytes:458 (458.0 B)

```

---

### Post by superprash2003 on 2008-06-20
you still dont seem to be getting an ip.. what is your your router's ip address? 192.168.1.1??

---

### Post by izak on 2008-06-21
Indeed, I still can't access the router at [http://192.168.0.1](http://192.168.0.1). 

Don't know if it might help but I've added two screenshots of the network manager GUI.There's nothing going on in the 'location' bar and IP adress is still masked out there as well.

In the ifconfig output, why are there two eth0 instances? One doing the sending and receiving without the IP adress and the other, eth0:avahi, that apparently refers to the same hardware and has an IP adress but does not send or receive data?

---

### Post by superprash2003 on 2008-06-21
ok go to system->administration->network and go to eth0 properties and set it to Static Ip address. now enter the ip address as 192.168.0.10 ..and gateway as 192.168.0.1 .. now are you able to access [http://192.168.0.1](http://192.168.0.1)

---

### Post by izak on 2008-06-21
Thank you, after changing those parameters I could connect to the router again. However, I could no longer connect to the internet (using pppoeconf).

Also, getting back to the reason I wanted to connect to the router: it appears that one cannot set the DNS on the router when it is in (modem only) bridge mode. To access the page where DNS settings are applied the router must be set to (router+modem) mode. After changing to modem+router mode I could connect to the internet again.

Well, I&#314;l try OpenDns in (modem+router) mode then, thanks.

---

### Post by modmotors on 2011-04-05
Hi
I have ubuntu lucid and have just got a new wireless router called an edup EP-DL520G and it doesnt seem to work on linux as the disc only has windows and mac driver. any ideas on how to get it working?

---

