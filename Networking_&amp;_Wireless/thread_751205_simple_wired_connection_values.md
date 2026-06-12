---
title: "simple wired connection values"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by cortical on 2008-04-10
An Ubuntu 7.10 box I am using as a test mule, in setting up a static IP for connection to another box (a Mac), there is a discrepancy for eth0 between Network and Network tool IP and Netmask values. Shouldn't  these be the same?

System:Admin:Network:Connections:Wired:Properties:
Wired connection	enabled
Roaming	disabled
Config	Static IP address
IP	10.10.10.1
Subnet mask	255.0.0.0
Gateway address	(blank)


If i then do:
sudo ifconfig eth0 10.0.0.2  netmask 255.255.255.0 up

I get :
cb@lx:~$ sudo ifconfig eth0 10.0.0.2 netmask  255.255.255.0 up
cb@lx:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:DC:1D:AB:AC  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6090 (5.9 KB)  TX bytes:4544 (4.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

cb@lx:~$


Checking Network Tools -  Network device eth0 shows the config 10.0.0.2/255.255.255.0 result from the terminal command for eth0
clicking configure, goes to eth0 properties, and the static IP address, has 10.10.10.1, 255.0.0

Why the disjoint between the terminal and Network Tools values for eth0, and Network Settings wired connection properties?

---

