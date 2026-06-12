---
title: "Accessing Router from Ubuntu Box"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by dtuza on 2009-02-04
Hi guys, I have a pretty newbie-level question.  I currently have a PPPoE connection set up on my Ubuntu box here - problem is, I can't access my router. I can access it using my girlfriend's (Vista) laptop at your usual 192.168.1.1 but I get nothing from here.  I assume it must be something in the way I have my connection set up - thoughts?

```
dtuza@Westeros:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:d9:a2:5c  
          inet6 addr: fe80::21d:7dff:fed9:a25c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1753111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1374162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1712306099 (1.7 GB)  TX bytes:351868567 (351.8 MB)
          Interrupt:221 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:a0:cc:58:9f:e8  
          inet6 addr: fe80::2a0:ccff:fe58:9fe8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:13 dropped:0 overruns:0 carrier:26
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xce00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:119786 (119.7 KB)  TX bytes:119786 (119.7 KB)

pan0      Link encap:Ethernet  HWaddr fe:db:31:a6:f9:8e  
          inet6 addr: fe80::fcdb:31ff:fea6:f98e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:540 (540.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:124.170.179.106  P-t-P:203.55.231.88  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:10351 (10.3 KB)  TX bytes:5000 (5.0 KB)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:124.170.147.53  P-t-P:203.55.231.88  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1752231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1373449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1673690354 (1.6 GB)  TX bytes:321605470 (321.6 MB)
```

---

### Post by Jynxx on 2009-02-04
I have a linksys router as well. Are you running wireless or cable into the router?

---

### Post by LowSky on 2009-02-04
Some people when they set up their router initially use MAC address filtering, which only allows computer with a certain mac addresss to access the router and therefor the internet, you need to disab;e this feature and use another method of blocking out other users, for instance I use WPA2 and turned off broadcasting of the name of the signal.

---

### Post by cerealtx on 2009-02-04
do you have connectivity on the nix computer? try pinging the gateway (192.168.1.1) see if you get responses

---

### Post by linux6994 on 2009-02-04
Your router should be handling the PPPoe function on its WAN port and then on the LAN port you can run DHCP or Static which ever you want on the PCs.

ISP >>> PPPOE >>> >>> >>> Router >>> >>> >>> PCs (DNS & GW pointing to router IP 192.168.1.1)

---

### Post by dtuza on 2009-02-04
Hi guys, thanks very much for your responses.

> I have a linksys router as well. Are you running wireless or cable into the router? 

I'm wired in via LAN, eth0 would be the connection in question.  The router is a Netcomm, model NB9WMAXX.  I did check their site but was unable to find any Linux support :(

> Some people when they set up their router initially use MAC address filtering, which only allows computer with a certain mac addresss to access the router and therefor the internet, you need to disab;e this feature and use another method of blocking out other users, for instance I use WPA2 and turned off broadcasting of the name of the signal.

I don't *think* this would be the problem, but I can't really check :) I have toyed around with MAC filtering at one stage or another in the 3 months or so I've had the router, but I've never once had the ability to connect to the router directly, whether the MAC filter was on or not.  Currently, I believe it's on WEP security so that an iPhone can be connected.

> do you have connectivity on the nix computer? try pinging the gateway (192.168.1.1) see if you get responses

```
dtuza@Westeros:~$ ping 192.168.1.1 -c5
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

```

I do suspect it's a setting on the router that has been disallowing me, but I'm not confident enough with networking to really have a clue what it could be.

---

### Post by kestrel1 on 2009-02-04
If you are connecting to the router via ethernet, you shouldn't need PPPo-E set-up on you linux box.
Your ethernet port (eth0) needs to be set up to get an IP address from the router via DHCP. Once you get an IP address from the router you should get a connection.
You are not currently seeing the router, because eth0 is not configured correctly or at all.

---

### Post by dtuza on 2009-02-06
> **kestrel1 said:**
> If you are connecting to the router via ethernet, you shouldn't need PPPo-E set-up on you linux box.
Your ethernet port (eth0) needs to be set up to get an IP address from the router via DHCP. Once you get an IP address from the router you should get a connection.
You are not currently seeing the router, because eth0 is not configured correctly or at all.
Thanks for this, have since resolved this by removing the old PPPoE settings and connecting as for your standard broadband connection.  Has made me realize what a shamefully limited understanding of networking I have.. marking this resolved :p

---

### Post by kestrel1 on 2009-02-06
Glad you are sorted.

---

