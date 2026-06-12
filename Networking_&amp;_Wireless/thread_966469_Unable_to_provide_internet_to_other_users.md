---
title: "Unable to provide internet to other users"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by diplomat.x on 2008-11-01
Alright, so i have the new ibex now. I am the admin and i have given two other accounts on which iam unable to provide ADSL internet. It can be accessed through my account. Please show me the way. 

Thanks in advance.

---

### Post by diplomat.x on 2008-11-03
Bumpy !!!

---

### Post by conscious on 2008-11-03
Why? Do you have to run something that requires root privileges?

---

### Post by silverglade00 on 2008-11-03
I think he's saying that he has a DSL connection that works under his account (which has admin privs) but not under other accounts on the machine. 

diplomat.x, is your connection pppoe?

---

### Post by superprash2003 on 2008-11-03
have you configured it via pppoeconf?

---

### Post by diplomat.x on 2008-11-04
I didnt do anything to get my net working. It just works when connected. I have an ADSL router connected through ethernet.

---

### Post by diplomat.x on 2008-11-05
Help Please

---

### Post by superprash2003 on 2008-11-06
go to the terminal and type ifconfig and post output.. you may be having ip problems..

---

### Post by diplomat.x on 2008-11-07
```
ABC@The-C2D-Machine:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:ce:69:ab  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fece:69ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2121297 (2.1 MB)  TX bytes:426823 (426.8 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

```

---

### Post by diplomat.x on 2008-11-07
Bump

---

### Post by superprash2003 on 2008-11-10
in your terminal type ping 192.168.1.1 and post output here..

---

