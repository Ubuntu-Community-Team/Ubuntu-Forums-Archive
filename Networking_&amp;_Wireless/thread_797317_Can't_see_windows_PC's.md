---
title: "Can't see windows PC's"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by jjascarm on 2008-05-17
I can't see my windows PC's when using Places|Network. When I open the network from here I get a Windows Network icon, but when I double-click on it I don't get anything.
I believe that it may be due to the fact that I have two network cards.
Eth0 (IP 192.168.1.21) manually configured which is a crossover cable to my Netgear digital entertainer and Eth1 which is DHCP for my internet. 
When I try to ping the other PC's it times out.
I think it is trying to connect on the wrong network card because when I use terminal to ping I get the following:
```
From 192.168.1.21 icmp_seq=1 Destination Host Unreachable

```

Any help would be appreciated

---

### Post by PryGuy on 2008-05-17
you can't even ping the host. show us output of the 'route' and 'ifconfig' commands

---

### Post by jjascarm on 2008-05-17
After typing route in terminal:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth1

```

After typing ifconfig in terminal:
```
Link encap:Ethernet  HWaddr 00:09:5b:1b:6a:79  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe1b:6a79/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14823490 (14.1 MB)  TX bytes:2924026 (2.7 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:02:44:72:57:cb  
          inet addr:192.168.1.21  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe72:57cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:911 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:318857 (311.3 KB)
          Interrupt:20 Base address:0x9800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65294 (63.7 KB)  TX bytes:65294 (63.7 KB)
```

Thanks for your help...

---

### Post by PryGuy on 2008-05-17
What's the IP of your Windows machine?

---

### Post by jjascarm on 2008-05-17
I have two windows PC's - my wife's laptop is 192.168.1.101 and my kids PC is 192.168.1.5

Thanks

---

### Post by PryGuy on 2008-05-17
Your ifconfig clearly shows that it is eth1 that has 192.168.1.21 and not eth0 as you wrote in your first post. Maybe you've messed up with your interfaces?

---

### Post by manosone on 2008-05-17
Alo.Well i got the same problem.If anynone could give me hand here..

route

10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.0.0.138      0.0.0.0         UG    100    0        0 eth0


ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1b:38:5e:77:97  
          inet addr:10.0.0.19  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe5e:7797/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62371910 (59.4 MB)  TX bytes:3099434 (2.9 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74400 (72.6 KB)  TX bytes:74400 (72.6 KB)


The ip of my windows machine is 10.0.0.9

---

### Post by PryGuy on 2008-05-18
manosone, your default route is 10.0.0.138, seems pretty strange to me 'cause none of your machines has such address. Do you have a machine with such addess in your network? Try changing your IPs from 10.0.0.X to 192.168.0.X, where X is the IP addesses of your machines. Just a thought.

EDIT: That's why I love DHCP! ;)

---

### Post by manosone on 2008-05-18
well pry i have manual configured the settings and i wrote on eth0 the 10.0.0.138 as a default gateway.Finnaly it worked.With the dhcp it didnt.I finally mounted the windows shared disc and i set it to remember the pass forever.Unfortunately when i logged in again it disapeared from the "places".Kinda off topic but any ideas about that?

---

### Post by Iowan on 2008-05-19
> **jjascarm said:**
> I think it is trying to connect on the wrong network card because when I use terminal to ping I get the following:
Two network cards in the same subnet seems like it could cause problems.  Could eth0 (and the Netgear digital entertainer) be reconfigured -  to use eg. 192.168.2.X?

---

