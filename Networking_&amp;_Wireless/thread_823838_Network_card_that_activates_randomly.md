---
title: "Network card that activates randomly"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by Aniki_Yukame on 2008-06-09
Hi:

I have already switched to ubuntu some time ago. In college i always use the wireless internet which runs without any problem. Now that i came back to my house, the connection we use here is through pppoe using wifi so i dont have access to anything else except my computer. Originally the connection didn't have any problem. I used sudo pppoeconf and there was no problem. But the other day after i updated the bios to the latest version,this finally allowed the fn keys to work.But when i boot my laptop for some reason the network card isn't active but it is still recognized. 

My laptop is a Toshiba Satellite A105-S4334 and the network card is a Intel PRO/100 VE Network Connection.

After i boot this is what ifconfig shows:

```
aniki@aniki-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79200 (77.3 KB)  TX bytes:79200 (77.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:b4:57:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-B4-57-84-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

The ethernet connection doesnt appear. So:

```
aniki@aniki-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:61:0a:ae  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

It is recognized but it isnt active. I tried to activate it manually.

```
aniki@aniki-laptop:~$ sudo ifconfig eth0 up
SIOCSIFFLAGS: Resource temporarily unavailable
```

but to no avail. At some forum i read that i should shut it down first.

```
aniki@aniki-laptop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
```

Suddenly after some reboots

```
aniki@aniki-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:61:0a:ae  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5460 (5.3 KB)  TX bytes:12073 (11.7 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:a0:d1:61:0a:ae  
          inet addr:169.254.6.244  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77485 (75.6 KB)  TX bytes:77485 (75.6 KB)

```

I hope anybody can help please.

Thanks in advance.

---

