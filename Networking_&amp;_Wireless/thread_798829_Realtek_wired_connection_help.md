---
title: "Realtek wired connection help"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by faytmye on 2008-05-18
hello everyone, i am currently having a problem with connecting to the internet on hardy, would appreciate it if anyone could help me!

(Apologies in advance as this is my first experience with linux)

Im trying to connect via a wired connection - *Realtek RTL8139/810x Family Fast Ethernet NIC*, dual booting with XP (which connects fine), using a linksys router (wired). I am able to ping my IP address but cannot connect to router inside firefox. 

Here is my ifconfig settings

```

stephen@stephen-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e6:2a:ab:3c  
          inet6 addr: fe80::20a:e6ff:fe2a:ab3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xd400 

eth0:avahi Link encap:Ethernet  HWaddr 00:0a:e6:2a:ab:3c  
          inet addr:169.254.6.45  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:124645 (121.7 KB)  TX bytes:124645 (121.7 KB)


```

my router address is 192.168.1.100 but even that wont show up. ive tried static ip connection as well as dhcp but to no avail.

im running on really old hardware and i wouldnt be surprised if the network card wasnt supported.

thanks in advance

stephen

---

