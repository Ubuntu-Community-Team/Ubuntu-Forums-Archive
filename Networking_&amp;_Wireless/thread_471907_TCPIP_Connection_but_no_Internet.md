---
title: "TCP/IP Connection but no Internet?"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by butlerapatrick on 2007-06-12
OK here is what I have going on. I have seven computers connected to a switch. The switch is connected to a router. Two cable modems are connected to the router and another computer. On the switch two of the computer are running Windows XP. Two of the computers are running Ubuntu and one is running Kubuntu. I have tcp/ip connection. I have pinged all the other interfaces with no problems. I have no problem pinging the other computers on the network. The two computers running XP have no problem getting to the web. One of the computers running Ubuntu has no problem getting to the web. But the other computer running Ubuntu and Kubuntu can not get to the web. I have run a trace route test on one of google's ip address, and that worked fine. In a terminal, I can ping the same address and I can ping [www.google.com](www.google.com). I can not however get the web browser to connect to the web site or the ip address. Help!!!!

---

### Post by aliyanage on 2007-06-12
Hi, 

could you please open a terminal and type the following command and post the output on here? 

```
ifconfig
```


regards
aliyanage

---

### Post by butlerapatrick on 2007-06-12
cable@cable-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:27:BE:8D:F9  
          inet addr:75.111.1.236  Bcast:75.111.1.255  Mask:255.255.255.192
          inet6 addr: fe80::290:27ff:febe:8df9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6654401 (6.3 MiB)  TX bytes:577056 (563.5 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83636 (81.6 KiB)  TX bytes:83636 (81.6 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.132.1  Bcast:192.168.132.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.26.1  Bcast:192.168.26.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by aliyanage on 2007-06-12
okay...
I had the same issue but I don't know whether the cause of this is the same as it was mine. The problem I had was that after I installed vmware I couldn't get out to the web anymore... did you install vmware?


regards
aliyanage

---

