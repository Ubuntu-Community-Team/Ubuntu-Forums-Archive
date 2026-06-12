---
title: "I think im close...but not there...help?"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by Virtuosity0021 on 2006-08-05
Alright, so ive been having trouble connecting to my internet.  After giving up on trying to set it up through the terminal, I decided to go through networking.

I first disabled everything.  Then under eth1, i put in the ssid i connect to, IP, Mask and Gateway and my WEP key.  After all this, i clicked ok, and clicked activate for eth1.  I then get an error message stating that i cannot connect and to make sure i am connected to the internet and that everything is turned on.  Right after, i logged onto windows, and the internet works fine.

Any help?

Thanks.

---

### Post by Sam Lars on 2006-08-05
Could you post the output of iwconfig and ifconfig?

---

### Post by Virtuosity0021 on 2006-08-11
Sorry for the delay.  

ifconfig (just the wireless one)
> **eth0**           Link encap:Ethernet  HWaddr 00:0B:DB:2D:8A:58
               UP BROADCAST MULTICAST  MTU:1500  Metric:1
               RX packets:0 errors:0 dropped:0 overruns:0 frame:0
               TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
               collisions:0 txqueuelen:1000
               RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
               Interrupt:201


iwconfig (just eth1 again)
> **eth1**           IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
               Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
               RTS thr:off   Fragment thr:off
               Link Quality:0  Signal level:0  Noise level:0
               Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
               Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Thanks again for any help with this issue of mine.

---

### Post by Virtuosity0021 on 2006-08-12
Anyone?

---

