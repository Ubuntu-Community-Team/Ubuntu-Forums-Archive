---
title: "Cannot connect to internet by a Sagem 1400W"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by ronniegaucho on 2008-02-10
Hi, I've just installed Ubuntu 7.10 (with Dual-Boot), but I can't open a website or download a packadge with Synaptic. When I go on Windows, internet works perfectly. My router (Sagem 1400W) is connected to the computer by Ethernet. Please, can you tell me what is the problem? Thank you

Excuse my english, I'm french.

---

### Post by Hightide on 2008-02-10
Hi

can you post output of 

ifconfig

if you dont know got to Applications\accessories\terminal and type the command

regards

:)

---

### Post by ronniegaucho on 2008-03-05
ifconfig returns:

```

eth0    Lien encap:Ethernet  HWaddr 00:0F:FE:42:5C:A8  
          inet adr:192.168.1.10  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::20f:feff:fe42:5ca8/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:34 erreurs:0 :0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:5379 (5.2 KB) Octets transmis:12921 (12.6 KB)
          Interruption:16  

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:336 erreurs:0 :0 overruns:0 frame:0
          TX packets:336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:16800 (16.4 KB) Octets transmis:16800 (16.4 KB)

```

---

