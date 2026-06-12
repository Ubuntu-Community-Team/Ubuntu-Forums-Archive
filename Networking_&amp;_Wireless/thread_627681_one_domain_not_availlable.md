---
title: "one domain not availlable"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by guillaume25 on 2007-11-30
Hi,

I've resently installed ubuntu 7.10 on my laptop. (my first linux install)

I have one Problem. everything else is number 1!!

here is the trouble:
One web site is not accessible on any browser.
but when I ping it, I receive 100% positive reply...

other machine from the same local network can visit the web site with out any problem

here is some info for my machine:

guillaume@guillaume-laptop:~$ ifconfig
eth0      Lien encap:Ethernet  HWaddr 00:A0:D1:45:71:C6  
          inet adr:192.168.1.202  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::2a0:d1ff:fe45:71c6/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:4780 erreurs:0 :0 overruns:0 frame:0
          TX packets:4026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:3455169 (3.2 MB) Octets transmis:860577 (840.4 KB)

eth1      Lien encap:Ethernet  HWaddr 00:13:02:84:5E:2F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :7968 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)
          Interruption:18 Adresse de base:0x4000 Mémoire:da000000-da000fff 

eth1:avah Lien encap:Ethernet  HWaddr 00:13:02:84:5E:2F  
          inet adr:169.254.4.7  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interruption:18 Adresse de base:0x4000 Mémoire:da000000-da000fff 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:2880 erreurs:0 :0 overruns:0 frame:0
          TX packets:2880 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:2777860 (2.6 MB) Octets transmis:2777860 (2.6 MB)
________________________________

Périphérique réseau :	lo
Adresse matérielle :	Loopback
Adresse IP :	127.0.0.1
Masque de réseau :	255.0.0.0
Diffusion :	 
Multicast :	Désactivé
MTU :	16436
Vitesse du lien :	 
État :	Actif
Paquets transmis :	2914
Erreurs de transmission :	0
Paquets reçus :	2914
Erreurs de réception :	0
Collisions :	0

________________________________
here is the ping results:

Octets	Source	Seq	Temps	Unités
64	66.11.175.146	1	51.8	ms
64	66.11.175.146	2	52.1	ms
64	66.11.175.146	3	51.7	ms
64	66.11.175.146	4	51.8	ms
64	66.11.175.146	5	53.1	ms
Temps minimum :	51.70 ms
Temps moyen :	52.05 ms
Temps maximum :	53.10 ms
Paquets transmis :	5
Paquets reçus :	5
Paquets reçus avec succès :	100%

________________________________________

what should I look for now...

please help.

thanks

---

