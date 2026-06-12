---
title: "Slow internet"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by kazbear on 2007-01-14
I bricked my linksys WR54G.  My replacement is a Zyxel x-550.  Since then, my Ubuntu boxes have very slow internet responce time.

I have 2 Ubuntu boxes, one wireless, one wired.  They both respond the same way.  With the Linksys, all was ok.  The only change I made was the Zyxel and now its quite frustrating.

I also have two XP boxes and they respond the same way as they did before with the Linksys.

Is there something I can look at to fix this?

Thanks
-kaz

---

### Post by mkoyle on 2007-01-15
My first guess is that your new Zytel router tells clients it is a DNS server but doesn't respond when DNS requests come in.  I have seen this problem with certain routers.  To see if this is the problem, someone smarter than me will want some information.

Post here the contents of the file /etc/resolv.conf

gedit /etc/resolv.conf

should get the contents and you can paste them here.

While you are at it, it could possibly be helpful to see a couple other things, too.  Open a terminal and run 

ifconfig

and

route

and post the output here as well.  One last thing that might be helpful to someone would be the output from one of your windows systems.  Start-->run-->cmd.  Then type (forgive me if I am wrong... Windows ... oh, well) ipconfig /all

With these, someone can probably sort out what the problem is.

--Matthew

---

### Post by kazbear on 2007-01-15
/etc/resolv.conf
```
nameserver 192.168.1.254

```

ifconfig
```
ath0      Link encap:Ethernet  HWaddr 00:11:95:4A:10:C2  
          inet addr:192.168.10.160  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe4a:10c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18668778 (17.8 MiB)  TX bytes:3283664 (3.1 MiB)

eth0      Link encap:Ethernet  HWaddr 00:D0:59:1C:5F:B5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:548 (548.0 b)  TX bytes:548 (548.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-4A-10-C2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72720 errors:0 dropped:0 overruns:0 frame:999
          TX packets:18774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:23716204 (22.6 MiB)  TX bytes:3708272 (3.5 MiB)
          Interrupt:11 Memory:d0ba0000-d0bb0000 
```

$ route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    *               255.255.255.0   U     0      0        0 ath0
default         192.168.10.1    0.0.0.0         UG    0      0        0 ath0

```

---

### Post by kazbear on 2007-01-16
in case someone was curious, I solved my problem.  Just search for IPV6.  Made some chenges with Firefox and all is back to normal.

---

### Post by mkoyle on 2007-01-22
Glad you got that fixed.  Sorry I didn't make it back sooner.

--Matthew

---

