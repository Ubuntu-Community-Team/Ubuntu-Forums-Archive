---
title: "no connection"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by zdubun on 2010-09-06
My Ubuntu on my double booted laptop was working fine. Now about 4 days ago I have no connection. Prior to this I had no problems. I can see that the WIFI card is on but there is no network detection.  I donot even have a connection if I attached the cable from the router. Going thru terminal shows no connection.
I donot have any problem in Windows. 
In my system, I can only see Network Connections. Is Network manager supposed to be a seperate utility. If so I cannot see it.

Regards

---

### Post by Chesamo on 2010-09-06
Open Terminal, and try this command. ```
gksudo network-manager-gnome
```

---

### Post by jtarin on 2010-09-06
Just about time to pay your wireless bill.....did you forget the first of the month?

Lets see the results of the command ```
ifconfig
```

What did you upgrade about that time?
What version of Ubuntu are you running?

---

### Post by zdubun on 2010-09-18
H there, I am pasting the output, :-
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

