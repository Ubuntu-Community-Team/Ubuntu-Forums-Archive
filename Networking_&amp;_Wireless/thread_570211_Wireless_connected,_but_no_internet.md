---
title: "Wireless connected, but no internet"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by Kevin J on 2007-10-08
Hello all,
I downloaded ubuntu 7.04 and the internet worked well
After rebooting I could not get an internet connection.
I reset the configuration to 'enable roaming'. This has led to an icon, four bars, saying that I have 'wireless connection to 'linksys' ' at 89%.
I am unable to access the internet. 
NOt sure what to do next, can anyone help?

Kevin Jones

---

### Post by rg_stephens on 2007-10-08
I'm not sure. Are you sure that "linksys" is a working connection?  Have you tried disabling the connection for a few seconds, and then re-enabling it? 

If you still are having problems, to the terminal and type ifconfig, and post the results.

Some people recommend using a program called Wicd instead of Network Manager. 
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Kevin J on 2007-10-08
these are teh results
kevin@kevin-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:D1:FC:FA:A7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Base address:0xecc0 Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b) 

rausb0    Link encap:Ethernet  HWaddr 00:12:17:7C:66:89  
          inet6 addr: fe80::212:17ff:fe7c:6689/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:9320068 (8.8 MiB)  TX bytes:126684 (123.7 KiB) 

kevin@kevin-desktop:~$ 

any help?

kevin

---

### Post by Kevin J on 2007-10-08
Thanksfor the help!!! wireless now working.
I was adjusting the manual configuration and the internet now works.
MY problem is that I was adjusting the settings one by one with no plan in mind.
Presto it works! but I cannot remember exactly what I did.
This happens to me all the time

any way...thanks for the great support,

Kevin

---

### Post by rg_stephens on 2007-10-08
Yeah that happens to me all the time. 

Good luck!

---

