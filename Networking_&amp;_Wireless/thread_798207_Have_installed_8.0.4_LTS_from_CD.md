---
title: "Have installed 8.0.4 LTS from CD"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by accodata on 2008-05-18
Hi

I got frustrated at something else so I downloaded the new ubuntu and it keeps telling me I have a network manager error, and it will not allow me to connect at all to the internet, 

Please can someone help this newbie, to get the pc back online.

thanks

---

### Post by tamoneya on 2008-05-18
we are always glad to help and welcome.  What is the output of ```
ifconfig
```This should be typed into terminal (applications -> accessories -> terminal).

---

### Post by accodata on 2008-05-18
ifconfig
eth0 Link encap:Ethernet  HWaddr 00:0d:61:ce:16:ae
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:20 errors:0 dropped:0 overruns:0 frame:0
TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes 1232 (1.2)   TX bytes:7143  (6.9 KB)
Interrupt:17 Base address:0xdc00


eth0:avahi Link Ethernet   HWaddr 00:0d:ce:16:ae
inet addr: 169.254.6.248 Bcast:169.254.255.255  Mask:255.255.0.0
UP BROADCAST RUNNING MUTLICAST  MTU 1500  Metric:1
Interrupt:17 Base address:0xdc00

lo    Link encap:Local loopback
inet addr:127.0.0.1 Mask: 255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436 Metric:1
RX packets:950 errors:0 dropped:0 overruns:0 frame:0
TX packets:950 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:48076 (46.9KB) TX bytes:48076 (46.9KB)

---

### Post by accodata on 2008-05-18
Hi All

Not sure, however I have fixed my problem, I would like to thank the person who was trying to help me.

thanks for your thought and time

:)

---

