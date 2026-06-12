---
title: "Ubuntu 8.04 32bit unable to connect to the net"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by newbuntuxx on 2008-05-07
Hi,

I recently installed ubuntu 8.04. I also have xp on the same machine. 

At first, the internet connection was working fine with ubuntu. However, after I mounted my ntfs drives and rebooted, I lost the connection. I tried a few things here and there, but was unable to restore the connection. 

I have cable internet. IP given automatically (dhcp). I use a linksys router. I tried the connection with the router and without it: same results. (note that my connection in xp works just fine, so, it cant be a hardware problem).

Here is some ubuntu info that might help:

```
ali@ali-ubuntu:~$ sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:9d:27:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:2 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Memory:cffc0000-d0000000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:8c:9d:27:94  
          inet addr:169.254.6.142  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Memory:cffc0000-d0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:3872 (3.7 KB)  TX bytes:3872 (3.7 KB) 
```


```
ali@ali-ubuntu:~$ sudo dhclient eth0 
There is already a pid file /var/run/dhclient.pid with pid 6161 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

Listening on LPF/eth0/00:1e:8c:9d:27:94 
Sending on   LPF/eth0/00:1e:8c:9d:27:94 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2 
No DHCPOFFERS received. 
No working leases in persistent database – sleeping. 
```




```
ali@ali-ubuntu:~$ sudo netstat -nr 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface 
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0 
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 eth0 

```

Also, here is a copy of my syslog:

[http://nahawand1.googlepages.com/syslogubuntu.odt](http://nahawand1.googlepages.com/syslogubuntu.odt)

or

[http://nahawand1.googlepages.com/syslogubuntu.txt](http://nahawand1.googlepages.com/syslogubuntu.txt)

any help is appreciated!

---

### Post by newbuntuxx on 2008-05-07
you may delete this topic, i posted it in the beginners section here is the link:

[http://ubuntuforums.org/showthread.php?p=4902758#post4902758](http://ubuntuforums.org/showthread.php?p=4902758#post4902758)

---

