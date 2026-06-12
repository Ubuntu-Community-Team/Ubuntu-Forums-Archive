---
title: "Regularly losing PPP connection"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by siepmann on 2007-09-04
I connect to the internet through a USB ADSL Alcatel modem.  I use the machine as a server, so it is left on all the time.  At the rate of roughly once a week, the connection drops, yet ifconfig still gives normal looking output:

```
eth0      Link encap:Ethernet  HWaddr 00:0D:87:9C:D5:20  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5306335 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10452333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:358498533 (341.8 MiB)  TX bytes:2624418491 (2.4 GiB)
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:409 errors:0 dropped:0 overruns:0 frame:0
          TX packets:409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38132 (37.2 KiB)  TX bytes:38132 (37.2 KiB)

ppp0   Link encap:Point-to-Point Protocol  
          inet addr:79.73.195.26  P-t-P:212.74.102.19  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:489471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:477111241 (455.0 MiB)  TX bytes:67831678 (64.6 MiB)

```

Any pointers gratefully received,

Peter

---

### Post by noob12 on 2007-09-04
[COLOR="Red"]Scratched this.  I didn't notice that you had the ppp link;  my comments don't apply.[/COLOR]

---

### Post by siepmann on 2007-09-04
I should add that I have tried 

```
pppd call speedtch
```

but it just says

```
connect(0.38): Address already in use
```

---

