---
title: "PPP0E Connection Problem"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by balachandarlinks on 2008-06-06
Hai,
  I m using ubuntu for the last one year...Two days before i installed ubuntu 8.04...After that i connect it to the net using UT300R2U ADSL2+ MODEM (BSNL BROADBAND CONNECTION)....
  i m using SUDO PPPOECONFIG command to Configure my eth0
  it works fine for the first time....
  when i login next time it doesnt connect anymore.....
  i use SUDO PON DSL-PROVIDER command to get connected....
  So that i use PLOG command to check my status....
       Jun  5 17:29:50 net-desktop pppd[10812]: Connection terminated.
       Jun  5 17:29:50 net-desktop pppd[10812]: Modem hangup
       Jun  5 17:30:20 net-desktop pppd[10812]: PPP session is 10764
       Jun  5 17:30:20 net-desktop pppd[10812]: Using interface ppp0
       Jun  5 17:30:20 net-desktop pppd[10812]: Connect: ppp0 <--> eth0
       Jun  5 17:30:22 net-desktop pppd[10812]: CHAP authentication   failed: The system is busy. Please retry later.
       Jun  5 17:30:22 net-desktop pppd[10812]: CHAP authentication failed
       Jun  5 17:30:28 net-desktop pppd[10812]: Connection terminated.
       Jun  5 17:30:28 net-desktop pppd[10812]: Modem hangup
       Jun  5 17:30:28 net-desktop pppd[10812]: Exit.


   But a comedy suddenly it is **connected** to net....after that too the PLOG command shows the same what is given above....
   
    Awaiting for the reply....:)

---

### Post by superprash2003 on 2008-06-06
please post your ifconfig output from the terminal

---

### Post by balachandarlinks on 2008-06-06
eth0      Link encap:Ethernet  HWaddr 00:19:d1:34:1a:c6  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe34:1ac6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5570 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4218266 (4.0 MB)  TX bytes:1839408 (1.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93200 (91.0 KB)  TX bytes:93200 (91.0 KB)
****




 But this time it is connected......I cant understand why it is happening like this....Is there any commands available for connecting,disconnecting,view status ..........
 please post it..........:)

---

### Post by superprash2003 on 2008-06-06
its porbably because you werent getting an ip from your router last time.. this time you got a 192.168.1.2 ...

---

### Post by balachandarlinks on 2008-06-07
Thanks........:guitar:

---

### Post by partha1045 on 2009-09-13
i cant connect my BSNL broadband UT300R2U modem in ubuntu 9.04 please help me

---

