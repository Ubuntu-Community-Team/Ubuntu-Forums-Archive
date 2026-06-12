---
title: "[SOLVED] Wireless connected,but i dont have internet"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by squeezah on 2008-03-28
Hi everyone.I need some help with my wireless.Iam using ubuntu for 1 month and everything worked fine until one day that while i was normal connected no internet:( i can ping my rooter but i cant get in its settings.:(( here some clues: 
>  sudo lshw -C network
 ```
 *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:64:90:ca
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2mprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.2.2 latency=32 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:06:09.0
       logical name: eth0
       version: 01
       serial: 00:40:ca:d1:5d:d9
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=32 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s
```

/*PINGSSS*/
192.168.2.1 is my router

> ping -c 3 192.168.2.1
```
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=0.041 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=0.042 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=0.040 ms

--- 192.168.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.040/0.041/0.042/0.000 ms
```


> ping google.com
```
ping: unknown host google.com
```


 > ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:40:CA:D1:5D:D9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:64:90:CA  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe64:90ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:131635 (128.5 KB)  TX bytes:4603 (4.4 KB)
          Interrupt:10 Base address:0x2000 Memory:b0108000-b0108fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56424 (55.1 KB)  TX bytes:56424 (55.1 KB)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

Also i have the same problem with wired connection...

---

### Post by chili555 on 2008-03-28
Hmmmmm!> vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.2.1Looks like 192.168.2.1 is the IP address of your virtual machine network interface, as well as the router! So, you are actually pinging yourself. Another clue is that the ping times are astoundingly fast.

I don't know much about virtual machines, but I'd suggest you fix that first and see if your trouble is gone.

---

### Post by superprash2003 on 2008-03-28
yes there is a ip conflict i feel..are you using eth0 or eth1 to connect to the internet.. hope this helps you [http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html](http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html)

---

### Post by squeezah on 2008-03-28
am using eth1.i tried to connect manual but some problem.i dont really understand what chili555 said about virtual:P

---

### Post by superprash2003 on 2008-03-28
so is your modem/router's ip 192.168.2.1??

---

### Post by squeezah on 2008-03-28
i think so.thats from windows and that ip i use to log in routers settings

---

### Post by superprash2003 on 2008-03-28
ok.. you need to change your vmnet8's ip to something else.. cause it says vmnet ip is 192.168.2.1 and your modem's ip is 192.168.2.1 .. so go to System->administration->network and go to the properties of vmnet8 and change from 192.168.2.1 so something else

---

### Post by squeezah on 2008-03-28
> **superprash2003 said:**
> ok.. you need to change your vmnet8's ip to something else.. cause it says vmnet ip is 192.168.2.1 and your modem's ip is 192.168.2.1 .. so go to System->administration->network and go to the properties of vmnet8 and change from 192.168.2.1 so something else

M8 thanx!!!!!!!!!!!!!!!everything ok now.Can i ask why in hell i had this problem while everything was working fine ?

---

### Post by superprash2003 on 2008-03-28
well the problem could have started as soon as you configured your vmnet to 192.168.2.1 causing a conflict with vmnet8 and your router

---

### Post by squeezah on 2008-03-28
the problem probably  was that i install vmware player for a project when i unistall it everything works fine:P

---

### Post by superprash2003 on 2008-03-28
well you can install vmware player again .. but make sure none of those vmnet cards get ips like 192.168.2.x

---

### Post by Eiríkr on 2008-03-28
Glad to hear things are working, squeezah.  :D  Since it sounds like you're all set, could you please set this thread to SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Cheers,

Eiríkr

---

