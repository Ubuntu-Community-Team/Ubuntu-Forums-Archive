---
title: "Slow wifi on one laptop fast ethernet"
date: 2013-12-26
forum: Networking &amp; Wireless
---

### Post by jcrouch074 on 2013-12-26
okay so instantly my wifi went nuts on one of my laptops. Its connected but takes like a minute to load the page or it doesn't even load at all. if i connect to the router with a cable it works just fine. i completely removed ubuntu and reinstalled and it does the same thing. i know for a fact theres nothing wrong with my wifi because my other devices work just fine.

---

### Post by PaulBx on 2013-12-26
See if you can find any issues in your logs. Show the results of ifconfig.

---

### Post by jcrouch074 on 2013-12-26
wlan1     IEEE 802.11bgn  ESSID:"FBISURVEILLANCE2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: B2:B2:DC:4D:82:9D   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

eth1      no wireless extensions.

lo        no wireless extensions.

amanda@halfpint-Satellite-C655D:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr e0:db:55:8b:2b:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54722 (54.7 KB)  TX bytes:32667 (32.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1499 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1499 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:116882 (116.8 KB)  TX bytes:116882 (116.8 KB)

wlan1     Link encap:Ethernet  HWaddr a4:17:31:03:f4:45  
          inet addr:192.168.0.117  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a617:31ff:fe03:f445/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3974 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4008086 (4.0 MB)  TX bytes:534720 (534.7 KB)

---

### Post by jcrouch074 on 2013-12-26
okay i don't freaking understand this but all of a sudden its back working. but ill we keep posting if anything further happens

---

