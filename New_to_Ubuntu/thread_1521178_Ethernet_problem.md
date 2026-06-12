---
title: "Ethernet problem"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by viditgoyal3009 on 2010-06-30
hello everyone...
i have recently installed ubuntu on my laptop but i am unable to connect to internet using by cable connection as my ethernet port seems to be not working... it used to work perfectly before i formatted my system....
Can anyone help please..

---

### Post by Rybandt on 2010-06-30
I just had this same problem on my desktop. What kind of computer do you have... I'm on lunch break so I will do some hunting for you.

---

### Post by viditgoyal3009 on 2010-06-30
hp mini 110

---

### Post by TeoBigusGeekus on 2010-06-30
Post us the output of 
```
ifconfig
```

---

### Post by Rybandt on 2010-06-30
from a quick google search that is an Atheros driver. give me a moment ):P

---

### Post by viditgoyal3009 on 2010-06-30
vidit@vidit-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 0c:60:76:5e:05:eb  
          inet6 addr: fe80::e60:76ff:fe5e:5eb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by viditgoyal3009 on 2010-07-21
someone please help me out...

---

