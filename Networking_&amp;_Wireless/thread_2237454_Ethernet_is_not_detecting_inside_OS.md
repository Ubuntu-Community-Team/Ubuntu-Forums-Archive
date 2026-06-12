---
title: "Ethernet is not detecting inside OS"
date: 2014-08-01
forum: Networking &amp; Wireless
---

### Post by rahbz on 2014-08-01
Hi all,

My laptop (HP DV6) is dual boot system. At the start of laptop I could see the light at the ethernet showing that it is connected. But once ubuntu or windows gets started, ethernet cable is not detected. Again there will be no issue for some particular ethernet cables.

> ifconfig eth0 
eth0      Link encap:Ethernet  HWaddr 64:31:50:62:91:24  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2318 errors:0 dropped:6 overruns:0 frame:0
          TX packets:1258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1208444 (1.2 MB)  TX bytes:196928 (196.9 KB)

---

### Post by yancek on 2014-08-01
> Again there will be no issue for some particular ethernet cables.

Are you saying that a particular ethernet cable won't work and another will?  Cables go bad, connections cab be bad.  More detail on the situation.

---

### Post by rahbz on 2014-08-01
Yah exactly, but that particular cable works perfectly fine in my friends laptop
also it seems to work during the startup (during bios screen)

---

### Post by rahbz on 2014-08-02
Updating kernel seems to change the drivers,
reinstalling the drivers did the job

---

