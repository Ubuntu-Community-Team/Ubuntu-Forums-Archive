---
title: "no connection part 2"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by zdubun on 2010-09-18
Just renewing the thread. My ubuntu does is not connecting to the net either thru cable or wifi. It is 10.04. Following is the result of two outputs. Any suggestions:-
 

zeek2@zeek2-laptop:~$ ifconfig
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:16436  Metric:1
              RX packets:12 errors:0 dropped:0 overruns:0 frame:0
              TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
    zeek2@zeek2-laptop:~$ iwconfig
    lo        no wireless extensions.
  eth0      no wireless extensions.
  eth1      IEEE 802.11  Access Point: Not-Associated   
              Link Quality:5  Signal level:0  Noise level:0
              Rx invalid nwid:0  invalid crypt:0  invalid misc:0
  pan0      no wireless extensions.
    zeek2@zeek2-laptop:~$

---

