---
title: "semi connection"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by alon30 on 2007-05-12
Hi, 
I can not connect to the internet, after a fresh install of 7.04.

the network manager icon in the top right has an icon that does not indicate any problem.
I have cable modem, which is connected to the pc with a standard network cable.

```
alon@alon-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:A2:3E:62  
          inet addr:172.28.14.232  Bcast:255.255.255.255  Mask:255.255.224.0
          inet6 addr: fe80::20e:a6ff:fea2:3e62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5055 (4.9 KiB)  TX bytes:5972 (5.8 KiB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


``` 

```

alon@alon-ubuntu:~$ nslookup www.digg.com
Server:         192.168.101.101
Address:        192.168.101.101#53

Non-authoritative answer:
Name:   www.digg.com
Address: 213.57.1.13


```


```

May 12 17:15:18 alon-ubuntu dhcdbd: Started up.
May 12 17:15:19 alon-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
May 12 17:15:19 alon-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
May 12 17:15:21 alon-ubuntu hpiod: 1.7.3 accepting connections at 2208... 
May 12 17:15:21 alon-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
May 12 17:15:21 alon-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May 12 17:15:21 alon-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
May 12 17:15:23 alon-ubuntu gconfd (alon-5642): starting (version 2.18.0.1), pid 5642 user 'alon'


```
please help.

---

### Post by kroiz on 2007-05-13
It seems to me that you are already connected (since you got an IP and DNS) maybe you just need to a dialer of some sort.
maybe your ISP could provide you with more information.

---

### Post by kroiz on 2007-05-13
I found this tutorial in hebrew.
[http://linux.israel.net/punbb/viewtopic.php?id=3098](http://linux.israel.net/punbb/viewtopic.php?id=3098)

---

