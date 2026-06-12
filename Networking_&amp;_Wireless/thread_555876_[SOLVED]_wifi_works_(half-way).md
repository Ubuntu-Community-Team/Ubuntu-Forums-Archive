---
title: "[SOLVED] wifi works (half-way)"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by MrBordello on 2007-09-20
Hi!
since the last update of my lovely Gutsy Laptop I got a strange "error": When I log in, my AP gets recognized and authenticates my PC - fine. So I open Firefox and nothing happens... here's the output of iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"UNICRON"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:04:0E:D8:36:F8   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=92/100  Signal level=-39 dBm  Noise level=-40 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:271   Missed beacon:0

```
seems OK to me... here's the output of ifconfig:
```

eth0      Protokoll:Ethernet  Hardware Adresse 00:16:36:E1:91:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Protokoll:Ethernet  Hardware Adresse 00:1B:77:2B:40:0C  
          inet Adresse:192.168.1.2  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6 Adresse: fe80::21b:77ff:fe2b:400c/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:271 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:6420 (6.2 KB)  TX bytes:16737 (16.3 KB)
          Interrupt:16 Basisadresse:0xe000 Speicher:d8000000-d8000fff 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

```
not ok. actually my AP has the 192.168.0.1 as its IP and mostly gives me something like 192.168.0.23...
Now comes the strange part. When I connect wired I get a working IP, after that, I pull out the cable and check back my wifi... and tada:
```

eth0      Protokoll:Ethernet  Hardware Adresse 00:16:36:E1:91:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1366 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:1236327 (1.1 MB)  TX bytes:220841 (215.6 KB)
          Interrupt:18 

eth1      Protokoll:Ethernet  Hardware Adresse 00:1B:77:2B:40:0C  
          inet Adresse:192.168.0.23  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::21b:77ff:fe2b:400c/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:284 overruns:0 frame:0
          TX packets:34 errors:0 dropped:3 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:9870 (9.6 KB)  TX bytes:23163 (22.6 KB)
          Interrupt:16 Basisadresse:0xe000 Speicher:d8000000-d8000fff 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

```
correct and working! I know Gutsy ain't stable - I'm just trying to help. Anyone else the same problem?

---

### Post by MrBordello on 2007-09-21
Ok, got it:
we have a shared internet-connection in my house and one of my wacky neighbors bought a new access point - mis configured it promptly and killed the complete in-house-network...

---

