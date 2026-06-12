---
title: "internet not working on ubuntu"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by ashish_envy on 2009-06-03
i m using ubuntu for a first time i m using 9.04 version

i m not able to start my internet on ubuntu but i m running windows on d other hand and my net is working absolutely fine on windows , bt it doesn't work on ubuntu ....

i m having 2 lan port on my cpu , and i have plug in my internet wire to my onboard port only and my external port is connected to pci slot and it is free.....

some body has suggested me to type following command 

[B]1 mii-tool
2 ifconfig 
3 sudo lshw -c network[/B]

and the following result are -


**ashish@ashish-desktop:~$[B] [B]_mii-tool_**[/B][/B]
SIOCGMIIPHY on 'eth0' failed: Operation not permitted
SIOCGMIIPHY on 'eth1' failed: Operation not permitted
SIOCGMIIPHY on 'eth2' failed: Operation not permitted
SIOCGMIIPHY on 'eth3' failed: Operation not permitted
SIOCGMIIPHY on 'eth4' failed: Operation not permitted
SIOCGMIIPHY on 'eth5' failed: Operation not permitted
SIOCGMIIPHY on 'eth6' failed: Operation not permitted
SIOCGMIIPHY on 'eth7' failed: Operation not permitted
no MII interfaces found


***ashish@ashish-desktop:~$ _ifconfig_***
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:84:be:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x1000 

eth1      Link encap:Ethernet  HWaddr 00:19:d1:13:4c:1f  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe13:4c1f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60 (60.0 B)  TX bytes:4044 (4.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1072 (1.0 KB)  TX bytes:1072 (1.0 KB)



**[I]ashish@ashish-desktop:~$ _sudo lshw -c network[_/I]**
[sudo] password for ashish: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth0
       version: 10
       serial: 00:e0:4d:84:be:e8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth1
       version: 01
       serial: 00:19:d1:13:4c:1f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ce:7d:35:39:6b:53
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



pls tell what to do now

---

### Post by marsrover on 2009-06-03
hmm you should get a different kind of internet 
internet works right out of the box with my wireless sprint card (only source of internet)

some companys use a password to get internet

mine

user name: user
password: user

if that works then great

user user is unerversal

try getting a different type of internet

maby somone here can help with the code

i don't know nothing:(

---

### Post by superprash2003 on 2009-06-03
post output of ping 192.168.1.1

---

### Post by rahulhada on 2010-06-09
i face the same problem if u find any solution then let me know.

Cheers!
Rahul Hada

---

### Post by dineshs on 2010-06-10
Please start a new thread with the following information 
1)what type of connection(DSL or dialup...)
2)Do you have a modem?
3)If yes how it is connected to your PC (serial port? USB ? wireless?or ethernet.
Also post what you get for
```
ifconfig -a
```
```
ping 4.2.2.1 -c5
```

---

