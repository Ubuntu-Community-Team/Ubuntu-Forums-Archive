---
title: "can't connect with wireless"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by dujlinvik on 2006-12-22
i'm trying to connect to the net for 4 days, and i'm really confused
my wireless card is configured properly (i hope so) :

dujlinvik@dujlinvik:~$ iwconfig ra0
ra0       RT2500 Wireless  ESSID:"ravangrad_kupusina"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:1 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=59/100  Signal level=-74 dBm  Noise level:-212 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dujlinvik@dujlinvik:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     *               255.255.0.0           U     0      0        0 ra0 

But i simply can't ping i.e. 169.254.0.1 (suppose that's my AP's address) and i don't know WHY?
firefox refuse to open any site....
what's wrong here?

---

