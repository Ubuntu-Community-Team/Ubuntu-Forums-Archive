---
title: "Server not found"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by SigmaHog on 2008-04-23
I have my wireless card working and can connect to the internet on other networks, but my network at home will not connect... it says im connected (usually from 62-71%) but everytime I open up FF it says server not found, I can't ping anything in the terminal either... any suggestions?

btw it's not encrypted or password protected at all...

---

### Post by superprash2003 on 2008-04-23
go to the terminal and type ifconfig and post results here.. It could be that you arent getting an ip from your router

---

### Post by SigmaHog on 2008-04-25
heres what ifconfig put out:

eth0      Link encap:Ethernet  HWaddr 00:15:C5:15:CF:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:16:CE:5E:E1:CD  
          inet addr:192.168.1.159  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::216:ceff:fe5e:e1cd/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:150 errors:0 dropped:683 overruns:0 frame:0 
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:19275 (18.8 KB)  TX bytes:8445 (8.2 KB) 
          Interrupt:4 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by SigmaHog on 2008-04-25
double post >.<

---

### Post by superprash2003 on 2008-04-25
mostly a DNS issue.. try changing your DNS servers to opendns .. read this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by SigmaHog on 2008-04-26
> **superprash2003 said:**
> mostly a DNS issue.. try changing your DNS servers to opendns .. read this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

nope thats a no go... im going to cry cause i really like ubuntu but can't get the internet while at home...

---

