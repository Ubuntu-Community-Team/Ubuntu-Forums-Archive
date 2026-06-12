---
title: "ubuntu 10.10 can't access other computers on LAN"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by itsols on 2010-11-24
My 10.10 laptop can't seem to access any computer on the lan.

All have static IPs and common netmask.

But on Windows, with the same settings, the Windows computers can talk to each other.

Any idea?

---

### Post by lmarmisa on 2010-11-24
Open a terminal, type this command and post its output:

```

ifconfig

```

---

### Post by itsols on 2010-11-24
here's my ifconfig's output:

eth0      Link encap:Ethernet  HWaddr 00:11:43:6e:b9:c1  
          inet6 addr: fe80::211:43ff:fe6e:b9c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19547 errors:2 dropped:1 overruns:0 frame:1
          TX packets:16196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10486412 (10.4 MB)  TX bytes:2526542 (2.5 MB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1488 (1.4 KB)  TX bytes:1488 (1.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:203.81.107.160  P-t-P:10.12.0.17  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:194973 (194.9 KB)  TX bytes:64329 (64.3 KB)

strangely, I can't even ping localhost!

---

### Post by itsols on 2010-11-24
correction:

I CAN ping localhost. But I CANNOT ping my own ip. 

eg: ping localhost ------ works
      ping 169.254.234.51 -------- does not work (it's the same machine)

---

### Post by lmarmisa on 2010-11-24
No IPv4 address is defined for your eth0 interface. This is your problem.

If you do not have a DHCP server in your LAN, you should config the interface manually. Try to use System -> Preferences -> Network connections.

You can see here the output of my command ifconfig:

```

luis@UB1004ENG:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 08:00:27:88:e5:93  
          inet addr:192.168.2.137  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe88:e593/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3709 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:404493 (404.4 KB)  TX bytes:34760 (34.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

luis@UB1004ENG:~$ 


```

---

### Post by itsols on 2010-11-24
Thank you it works!

But what I don't understand is that I had already made the changes in /etc/network/interfaces for static IP and this never worked.

Thanks anyway, it works now!

---

### Post by lmarmisa on 2010-11-24
Great!!!. :D

Please, mark the thread as SOLVED.

---

