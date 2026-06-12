---
title: "[SOLVED] Extremly slow network"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by Archmage on 2007-12-22
I hope that someone can help me. I want to set up an internet-router that should also be my fileserver. It has two network-cards in it one is 1Gbit, but my switch is still 100 Mbit, but since it is downward compatible it should still work at okay speed. I have a client with also a 1Gbit network card and was expecting okay speeds.

Unfortunatly it takes **10 hours** to copy 1 GB from the server to the client. SSH is hanging from time to time, etc.

Please help me to get a decent network-speed.

**Server:**

```
sudo ifconfig
eth1      Protokoll:Ethernet  Hardware Adresse 00:11:23:33:72:1F  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:991312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1122072 errors:0 dropped:0 overruns:8 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:719234630 (685.9 MB)  TX bytes:865317455 (825.2 MB)
          Interrupt:22 

eth2      Protokoll:Ethernet  Hardware Adresse 00:17:E5:13:93:5E  
          inet Adresse:192.168.0.100  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fd91::214:e6fe:fd16:944f/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93474 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:6412917 (6.1 MB)  TX bytes:132293325 (126.1 MB)
          Interrupt:20 Basisadresse:0xc000 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19194 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:5439467 (5.1 MB)  TX bytes:5439467 (5.1 MB)

ppp0      Protokoll:Punkt-zu-Punkt Verbindung  
          inet Adresse:84.142.78.206  P-z-P:217.0.116.100  Maske:255.255.255.255
          UP PUNKTZUPUNKT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:990278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1121714 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:3 
          RX bytes:697371051 (665.0 MB)  TX bytes:840608496 (801.6 MB)
```


**Client:**

```
sudo ifconfig
eth0      Protokoll:Ethernet  Hardware Adresse 00:17:D6:16:85:03  
          inet Adresse:192.168.0.200  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::217:e6ff:fe16:9502/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6688 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:3321473 (3.1 MB)  TX bytes:912422 (891.0 KB)
          Interrupt:11 Basisadresse:0xc000 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:2064 (2.0 KB)  TX bytes:2064 (2.0 KB)
```

---

### Post by Ocxic on 2007-12-22
if your computers are permanent look into NFS it's a networking file system and will allow you to access files from the server without transferring them to another PC first. I find ssh to be slow, but the speed your saying is way too slow. I also find that transferring anything to a windows PC takes longer then it should.

---

### Post by Archmage on 2008-01-16
Thanks for the reply and everybody else for reading it. I did find out that my switch was terrible broken. I did replace it and now everything is runing smoothly.

---

