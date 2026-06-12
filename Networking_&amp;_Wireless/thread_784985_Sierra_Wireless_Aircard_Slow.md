---
title: "Sierra Wireless Aircard Slow"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by rider_sss on 2008-05-07
hello ubuntu community...

since I updated to hardy y had some problems regarding my wireless internet connection. I use a Air Card 875u.

I can connect with kppp but if I open the firefox I won't load anything. 

Why is the conection so slow ? 

can you see an error in my network configuration ?

here my ifconfig
```
seba@seba-laptop:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:02:3f:95:0b:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Basisadresse:0x3000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:1508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1508 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX bytes:76296 (74.5 KB)  TX bytes:76296 (74.5 KB)

ppp0      Link encap:Punkt-zu-Punkt-Verbindung  
          inet Adresse:10.101.71.214  P-z-P:10.64.64.64  Maske:255.255.255.255
          UP PUNKTZUPUNKT RUNNING NOARP MULTICAST  MTU:1500  Metrik:1
          RX packets:7346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5365 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:3 
          RX bytes:10170173 (9.6 MB)  TX bytes:321644 (314.1 KB)


```

```
seba@seba-laptop:~$ route -n
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

Can you see any error in this configuration ? 

Please help !! I really need the internet !!!

---

