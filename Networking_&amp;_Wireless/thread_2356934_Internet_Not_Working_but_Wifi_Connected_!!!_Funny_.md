---
title: "Internet Not Working but Wifi Connected !!! Funny Problem"
date: 2017-03-28
forum: Networking &amp; Wireless
---

### Post by vaibhav05 on 2017-03-28
Hi all ,

I am in an funnny problem & am not able come to solution from last two days, i have two wifi(WLAN1 & WLAN2) connections in my building which i can use & one ethernet cable of the ISP which is connected to the  WLAN1.

I am using ubuntu 16.04 with following network configurations 


```
docker0   Link encap:Ethernet  HWaddr 02:42:e2:a2:d4:54  
          inet addr:172.17.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp7s0    Link encap:Ethernet  HWaddr 70:5a:0f:63:5e:04  
          inet addr:10.246.181.136  Bcast:10.246.255.255  Mask:255.255.0.0
          inet6 addr: fe80::6a33:cf39:44cd:f72e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16189 errors:0 dropped:475 overruns:0 frame:0
          TX packets:10387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17733073 (17.7 MB)  TX bytes:1053700 (1.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:22499 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22499 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1657305 (1.6 MB)  TX bytes:1657305 (1.6 MB)

wlp13s0   Link encap:Ethernet  HWaddr 44:1c:a8:03:a3:2f  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b024:b8b0:9664:964a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1261783 (1.2 MB)  TX bytes:194289 (194.2 KB)
```



From last two days i am not able to use the internet using the wifi , but when i plug the cable provided by my isp  directly into my ethernet port , internet is working, but not through wifi.

I researched more & i tried to Ping 8.8.8.8  & Ping google.com following are the results in both the WIFI's i am having 

WLAN1 

```
ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.0.1 icmp_seq=1 Destination Net Unreachable
From 192.168.0.1 icmp_seq=2 Destination Net Unreachable
From 192.168.0.1 icmp_seq=3 Destination Net Unreachable
From 192.168.0.1 icmp_seq=4 Destination Net Unreachable
From 192.168.0.1 icmp_seq=5 Destination Net Unreachable
From 192.168.0.1 icmp_seq=6 Destination Net Unreachable
From 192.168.0.1 icmp_seq=7 Destination Net Unreachable
^C
--- 8.8.8.8 ping statistics ---
7 packets transmitted, 0 received, +7 errors, 100% packet loss, time 6010ms


________________________________________________________________________________

When i pinged google.com following was the result 

vaibhav@vaibhav-HP-Notebook:~$ ping google.com
ping: unknown host google.com


```

Similarly i tested the same commands  in the Second Wifi at my home
WLAN2

```


vaibhav@vaibhav-HP-Notebook:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=47 time=51.6 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=47 time=42.7 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=47 time=45.6 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=47 time=43.4 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=47 time=42.4 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=47 time=43.0 ms
--- 8.8.8.8 ping statistics ---
8 packets transmitted, 6 received, 25% packet loss, time 7009ms
rtt min/avg/max/mdev = 42.495/44.820/51.628/3.220 ms

____________________________________________________________
When i pinged google.com following was the result

vaibhav@vaibhav-HP-Notebook:~$ ping google.com
ping: unknown host google.com

```

> Friends as you can see both the wifi's WLAN1 & WLAN2 is behaving differently 
i.e ping 8.8.8.8 & ping google.com is not working in WLAN1 
    ping 8.8.8.8 is working WLAN2 but ping google.com is not working in WLAN2

But the internet is working fine when i connect the ISP's cable directly to my ehtherent port 

I am frustrated trying everything i researched in these forums from last two day but nothing is working ,

Following are the some more info on the commands i executed in WLAN1

```

vaibhav@vaibhav-HP-Notebook:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1     0.0.0.0         UG    600    0        0 wlp13s0
link-local      *               255.255.0.0     U     1000   0        0 wlp13s0
172.17.0.0      *               255.255.0.0     U     0      0        0 docker0
192.168.0.0     *               255.255.255.0   U     600    0        0 wlp13s0

```

Anyone kindly suggest on how to overcome this problem 

Thanks & Regards
Vaibhav

---

### Post by vaibhav05 on 2017-03-28
[http://paste.ubuntu.com/24267393/](http://paste.ubuntu.com/24267393/) 
PASTEBINIT Link for neccesary info

---

### Post by Bucky Ball on 2017-03-28
Welcome. I can't help much, but I can say this. If you are trying to get wireless working, unplug the ethernet cable. That overrides the wireless connection and you will never get wireless working with the ethernet cable plugged in.

Forget about WLAN1 as you are not getting a connection there. Work on WLAN2 where you are able to ping.

So, with the ethernet cable unplugged and NO connection to WLAN1 (again, trying to connect to two access points at the same time is not going to work ordinarily and will stop any connection at all), does the WLAN2 wireless connection work as normal? If not, please let us know exactly what is happening with WLAN2 when you try to connect, say using Firefox. Forget about ethernet (unplug the cable for now) and WLAN1 (it is not connecting to the access point).

---

