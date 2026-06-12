---
title: "problems connecting to the internet"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by kiran.tambe08 on 2008-11-29
i use broadband connection i hav a ustarcom ut300r2u modem.
i typed sudo pppoeconf in the terminal then it said i found 1 device eth0 if all your devices were detected click yes. so i did n then i get this error  Sorry, I scanned 2 interfaces, but the Access            &#9474; 
          &#9474; Concentrator of your provider did not respond. Please    &#9474; 
          &#9474; check your network and modem cables. Another reason      &#9474; 
          &#9474; for the scan failure may also be another running pppoe   &#9474; 
          &#9474; process which controls the modem.

---

### Post by superprash2003 on 2008-11-29
in the terminal type ifconfig and post output .. in windows did you require a dialer to connect to the internet?

---

### Post by kiran.tambe08 on 2008-11-29
if dialer --->software in which i type my username and password n click connect then yes i do need a dialer

---

### Post by kiran.tambe08 on 2008-11-29
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:ba:ac:f6  
          UP 

BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 

dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 

overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX 

bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:ddec0000-ddf00000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1f:c6:ba:ac:f6  
          inet 

addr:169.254.11.88  Bcast:169.254.255.255  Mask:255.255.0.0
          UP 

BROADCAST MULTICAST  MTU:1500  Metric:1
          

Memory:ddec0000-ddf00000 

lo        Link encap:Local Loopback  
          

inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
 

         UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2144 

errors:0 dropped:0 overruns:0 frame:0
          TX packets:2144 errors:0 

dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          

RX bytes:107392 (104.8 KB)  TX bytes:107392 (104.8 KB)

---

### Post by superprash2003 on 2008-12-01
you have an ip address issue.. setup a static ip using this [http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html) and then run sudo pppoeconf

---

