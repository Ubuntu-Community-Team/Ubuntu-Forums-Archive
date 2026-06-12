---
title: "how to share internet connection  (2 ntWork adapts)"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by sam1948 on 2008-07-11
follow this it's quite simple
first open a terminal and run this:
```
ifconfig
```
don't close this one we. will use the information from there
u can see some thing like this
```

om:~$ ifconfig 
br        Link encap:Ethernet  HWaddr 00:02:2a:d2:22:9d  
          inet _addr:190.170.1.101_  Bcast:190.170.1.255  _Mask:255.255.255.0_
          inet6 addr: fe80::202:2aff:fed2:229d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11888 (11.8 KB)  TX bytes:27136 (27.1 KB)

eth0      Link encap:Ethernet  HWaddr 00:13:20:95:8d:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:02:2a:d2:22:9d  
          inet6 addr: fe80::202:2aff:fed2:229d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4375 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2795239 (2.7 MB)  TX bytes:825520 (825.5 KB)
          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80489 (80.4 KB)  TX bytes:80489 (80.4 KB)


```

open a terminal and run this:
```

sudo gedit $HOME/netdef

```

copy paste the following for** bridged connection with static** ip
```

#!/bin/sh
ifconfig eth0 0.0.0.0 
ifconfig eth1 0.0.0.0
brctl addbr br
brctl addif br eth0
brctl addif br eth1
ifconfig br _190.170.1.101_ netmask _255.255.255.0_ up
route add default gw _190.170.1.1_ 

```

the underlined ips should be replaced with it correlate underlined in the result of ifconfig (like in the example above).

```
sudo chmode +x $HOME/netdef
```
run the script and u done.
if u want it to run on startup. u can use System->Preferences->Startup Appl
then add a new item and browse for the script u just wrote in u'r home directory
**the problem it must be run as root.**
u can follow this thread about how to do that.
notice u have to give permissions to run the command inside the script
not the script itself
[http://ubuntuforums.org/showthread.php?t=1094008](http://ubuntuforums.org/showthread.php?t=1094008)
so instead u can add a line to /etc/rc.local
to run it. check and report if it worked 



and the following for bridged connection with dhcp
```

ifconfig eth0 0.0.0.0 
ifconfig eth1 0.0.0.0
brctl addbr br
brctl addif br eth0
brctl addif br eth1
ifconfig br up
route add default gw 190.170.1.1 
dhclient br

```


in both cases find out u'r dns server its probably u'r router (if u have one)

regards

---

