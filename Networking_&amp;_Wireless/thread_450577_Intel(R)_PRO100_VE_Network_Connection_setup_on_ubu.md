---
title: "Intel(R) PRO/100 VE Network Connection setup on ubuntu 7.04"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by moha_pagla on 2007-05-21
[COLOR="DarkOrange"][B]i just recently installed ubuntu 7.04.After installation i am unable to figure it out how to setup internet connection.
so plz help me.[/B][/COLOR]

---

### Post by insane_alien on 2007-05-21
tried plugging it into your router/modem?

---

### Post by Kobalt on 2007-05-21
Is the Intel PRO/100 VE an ethernet adaptator or a wireless card ?

---

### Post by moha_pagla on 2007-05-21
i think it a built in ethernet adapter

---

### Post by Kobalt on 2007-05-21
Can you please post the output of the following command line : ```
ifconfig
```

---

### Post by moha_pagla on 2007-05-21
ok then you have to wait 
i have to go to ubuntu 7.04 and come back then paste it

---

### Post by moha_pagla on 2007-05-21
eth0      Link encap:Ethernet  HWaddr 00:19:D1:37:AA:83  
          inet addr:10.0.30.36  Bcast:10.0.30.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe37:aa83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:195 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20080 (19.6 KiB)  TX bytes:3665 (3.5 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by insane_alien on 2007-05-21
its an ethernet card(well, a built in one). i have the same one.

---

