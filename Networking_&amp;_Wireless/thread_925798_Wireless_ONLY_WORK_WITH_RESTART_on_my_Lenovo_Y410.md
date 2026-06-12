---
title: "Wireless ONLY WORK WITH RESTART on my Lenovo Y410"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by deltamort on 2008-09-21
My wireless interface only works with a restart.
Could anyone who has experience in the problem help?

The wireless card is Intel Wireless 3945 ABG

At first bootup, iwconfig is like this:
> 
:~$ iwconfig

lo no wireless extensions.


eth0 no wireless extensions.


wmaster0 no wireless extensions.



After restarting, iwconfig can show my wireless interface (the mac add is replaced with X):

> :~$ iwconfig

lo no wireless extensions.


eth0 no wireless extensions.


wmaster0 no wireless extensions.


wlan0 IEEE 802.11g ESSID:"My Router" Nickname:""

Mode:Managed Frequency:2.462 GHz Access Point: XX:XX:XX:XX:XX:XX

Bit Rate=54 Mb/s Tx-Power=27 dBm

Retry min limit:7 RTS thr:off Fragment thr=2346 B

Power Management:off

Link Quality=92/100 Signal level=-38 dBm Noise level=-85 dBm

Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0

Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

