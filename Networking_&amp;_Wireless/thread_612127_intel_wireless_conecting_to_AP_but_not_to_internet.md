---
title: "intel wireless conecting to AP but not to internet"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by paolo.c on 2007-11-13
Hi, I have a travelmate c200 with an intel PRO 2915ABG on board, i can connect to an Access Point with DHCP active, key wpa, but no way to reach internet, i can ping  the other computer in the net (Win 2000) and the AC. Just installed ubuntu 7.10.

 i have the same problems with  another AP requerring manual configuration and a key wpa tkip.

could you help me?

Paolo

---

### Post by noob12 on 2007-11-13
Are you able to ping outside your local network if you use an ip address directly? For example:

```

ping 72.14.253.99

```

---

### Post by paolo.c on 2007-11-14
No, I can ping only my net addresses

---

### Post by noob12 on 2007-11-14
Can you post the output of these commands
```

ifconfig -a

route -n

```

---

### Post by paolo.c on 2007-11-14
I have tried to connect to two AP the fist one gives confiuration on eth0 (wire connection), the other to eth1 (wireless connection)

 ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:EE:B6:36  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:5F:15:11  
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe5f:1511/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:1 dropped:1 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2345 (2.2 KB)  TX bytes:5360 (5.2 KB)
          Interrupt:17 Base address:0x4000 Memory:b0016000-b0016fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:528 (528.0 b)  TX bytes:528 (528.0 b)

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
a@a-laptop:~$

---

### Post by noob12 on 2007-11-14
Do you have the same problem if you put eth0 down?

```

sudo ifconfig eth0 down

```

---

### Post by paolo.c on 2007-11-16
I can't go to the internet either with eth0 down. Connetcion information in nm-applet givies me IP address, broadcast address, subnetmask, default route (192.168.1.1), DNS (the same)

---

### Post by unoodles on 2007-11-16
I have the exact same problem. I am using an intel pro 3945abg on an inspiron 1420. When I find free access points, they show up in the nm-applet. After a few minuites I get connected. Then I run EtherApe [http://etherape.sourceforge.net](http://etherape.sourceforge.net) , and there a re lots of people. When I ping any one of them i get a reply, but when pinging google, it fails.
This is really annoying (I cant use internet!) :( , and I really need help.



Edit: while browsing i just found this thread [http://ubuntuforums.org/showthread.php?t=613450](http://ubuntuforums.org/showthread.php?t=613450) looks interesting, i havent had time to try.

---

