---
title: "ifconfig shows wireless as ethernet interface??"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by sandyd on 2009-09-27
i got a problem here.
the output of ifconfig shows
```

eth0      Link encap:Ethernet  HWaddr 00:22:19:f0:af:7a  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fef0:af7a/64 Scope:Link              
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1              
          RX packets:403005 errors:0 dropped:0 overruns:0 frame:0         
          TX packets:246862 errors:0 dropped:0 overruns:0 carrier:0       
          collisions:0 txqueuelen:1000                                    
          RX bytes:578504948 (578.5 MB)  TX bytes:33916616 (33.9 MB)      
          Interrupt:17                                                    

eth1      Link encap:Ethernet  HWaddr 00:26:5e:38:66:c5  
          inet6 addr: fe80::226:5eff:fe38:66c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:9 dropped:0 overruns:0 frame:662524
          TX packets:49 errors:5 dropped:0 overruns:0 carrier:0  
          collisions:0 txqueuelen:1000                           
          RX bytes:0 (0.0 B)  TX bytes:6138 (6.1 KB)             
          Interrupt:17                                           

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0                               
          RX bytes:1735431 (1.7 MB)  TX bytes:1735431 (1.7 MB)  

```while i know one of them (probably eth0 cause i don't use wireless that much)+(i see that i downloaded 578mb)

help?

i can detect wireless networks however. i don't have a wireless net in my hosue so i can't tell if it still works.

---

### Post by Iowan on 2009-09-27
My laptop (HP dv4) does the same thing - but since it works for both wireless (at WIFI hotspots) and wired (at home), I haven't tried to "fix" it.

---

### Post by Bölvaður on 2009-09-27
> **Iowan said:**
> My laptop (HP dv4) does the same thing - but since it works for both wireless (at WIFI hotspots) and wired (at home), I haven't tried to "fix" it.

same for my laptop

---

### Post by sandyd on 2009-09-28
ah. thanks for clarifying that

---

