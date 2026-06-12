---
title: "How did I disable my LAN/WLAN interfaces??"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by danube on 2007-12-23
Since I have followed a wiki to share my laptop's Internet connection via UMTS card with other clients, both LAN and WLAN connections fail, while the modem connection is still working.

The wiki told me, to share, I should do the following:
```
sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
sudo sysctl -w net/ipv4/ip_forward=1
sudo /etc/init.d/dnsmasq restart
sudo dpkg-reconfigure ipmasq
```

Now, when I try to connect to my home router via LAN, i do receive a valid IP adress and the designated DNS (which is my router at 192.168.2.1), but cannot even ping the DNS.

My ifconfig looks like this:
```
eth0      Protokoll:Ethernet  Hardware Adresse 00:17:A4:D0:D9:08  
          inet Adresse:192.168.2.102  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6 Adresse: fe80::217:a4ff:fed0:d908/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:1199 (1.1 KB)  TX bytes:1088 (1.0 KB)
          Interrupt:16 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

Anyone knows how to fix my connections? *HELP* [-o<

---

