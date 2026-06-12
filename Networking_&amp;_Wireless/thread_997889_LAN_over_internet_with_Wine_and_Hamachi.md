---
title: "LAN over internet with Wine and Hamachi?"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by nwarrenfl on 2008-11-30
Hello everybody!

I've installed LoTR: BFME2 with Wine and it runs very well!
Now i would like to create a LAN party and let others be able to join from internet. I heard Hamachi can be used for that.

I've configured Hamachi and it works, others can join the network, but they can't see the LAN party ingame (they are Windows users). I've read that Hamachi creates a network interface named ham0, maybe that this is the problem as Ubuntu uses eth0?

Here's my ifconfig command:
```

warren@warren-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:e3:9e:c7  
          inet adr:88.197.174.123  Bcast:88.197.174.123  Masque:255.255.255.255
          adr inet6: fe80::215:f2ff:fee3:9ec7/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:811921 erreurs:0 :0 overruns:0 frame:0
          TX packets:441465 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1092738002 (1.0 GB) Octets transmis:29452413 (29.4 MB)
          Interruption:21 Adresse de base:0xde00 

ham0      Link encap:Ethernet  HWaddr 72:92:b4:89:f2:0c  
          inet adr:5.109.198.53  Bcast:5.255.255.255  Masque:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:500 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:1178 erreurs:0 :0 overruns:0 frame:0
          TX packets:1178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:56688 (56.6 KB) Octets transmis:56688 (56.6 KB)

warren@warren-desktop:~$ 

```

What can i do?

Thanks in advance, kind regards.

---

### Post by nwarrenfl on 2008-11-30
Can someone help me? Thanks!

---

