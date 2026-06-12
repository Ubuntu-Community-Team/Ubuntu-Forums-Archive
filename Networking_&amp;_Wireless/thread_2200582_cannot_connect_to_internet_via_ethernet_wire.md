---
title: "cannot connect to internet via ethernet wire"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by Rio_Panji_Pangestu on 2014-01-20
dear bro or sis...
lately i cannot connect to internet with my ubuntu when i check ifconfig there is a report like this 
```
binsar@binsar-pc:~$ ifconfigeth0      Link encap:Ethernet  HWaddr 00:1f:e2:0b:04:7f  
          inet addr:192.168.88.42  Bcast:192.168.88.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e2ff:fe0b:47f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14374 errors:0 dropped:150 overruns:0 frame:0
          TX packets:1152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1664560 (1.6 MB)  TX bytes:94445 (94.4 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1051 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68154 (68.1 KB)  TX bytes:68154 (68.1 KB)



```

is there any one can help me with this

---

### Post by Rio_Panji_Pangestu on 2014-01-20
[FONT=comic sans ms]this noon i try too uninstall my ubuntu after everything fine and success with the uninstalling step, i continuing my process to re-installing it. after 1 hour i spend my time, i completely finish my re-installing. What i want to ask in here is why my internet connection cannot open via firefox, because i dont have any alternative web browser. can any one help me with this situation thx this is my if config report :

[/FONT]binsar@binsar-pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:e2:0b:04:7f  
          inet addr:192.168.88.42  Bcast:192.168.88.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e2ff:fe0b:47f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14374 errors:0 dropped:150 overruns:0 frame:0
          TX packets:1152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1664560 (1.6 MB)  TX bytes:94445 (94.4 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1051 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68154 (68.1 KB)  TX bytes:68154 (68.1 KB)

is there any strange thing or i just should re-install this computer again ?? please help me....

---

### Post by Kruppt on 2014-01-20
post output from: sudo cat < /etc/resolv.conf sudo cat < /etc/network/interfaces

---

### Post by Iowan on 2014-01-20
Looks like eth0 has been busy...
Can you** ping** the router/gateway?
Can you** ping** the Internet via IP? (try **ping 8.8.8.8**)
Can you** ping** by name? ( **ping google.com**)

---

### Post by Zhivargo on 2014-01-20
Do you have a Wifi router? 

can you login to the router?

```
route -n
```

type the default gateway into your browser. possibly
192.168.88.1 

post back

---

### Post by mörgæs on 2014-01-20
Please stop multiposting.
Merged.

---

### Post by Rio_Panji_Pangestu on 2014-01-20
dear lowan,
i can ping to router / gateway
but cannot ping to website ( google ) via name or ip

---

### Post by Rio_Panji_Pangestu on 2014-01-20
dear zhivargo when i route -n it become like this :

Kernel IP routing table         
Destination             Gateway              Genmask               Flags   Metric    Ref    Use       Iface
0.0.0.0                  192.168.88.1         0.0.0.0                  UG        0         0      0         eth0
169.254.0.0            0.0.0.0               255.255.0.0              U       1000      0      0         eth0
192.168.88.0          0.0.0.0               255.255.255.0           U         1         0      0         eth0

sorry it little bit mess

---

### Post by Rio_Panji_Pangestu on 2014-01-20
dear kruppt,
i already do what you tell and it become like this :

sudo cat </etc/resolv.conf
name server 127.0.0.1

sudo cat </etc/network/interfaces
auto lo
if face lo inet loopback

what can i do ?

---

### Post by Rio_Panji_Pangestu on 2014-01-20
dear morgaes i really sorry about multipos cause little bit panic on it i am sorry bro

---

