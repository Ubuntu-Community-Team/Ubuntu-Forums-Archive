---
title: "my IP adress is changed automaticly"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by jackm on 2008-05-02
Hi all,
I excute the following command to activate my eth0 :
```
sudo ifup eth0
``` 
when I execute **ifconfig** I get the following result:
```
eth0      Link encap:Ethernet  HWaddr 00:15:C5:17:2B:D8  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe17:2bd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22811 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17157553 (16.3 MB)  TX bytes:2852364 (2.7 MB)
          Interrupt:22 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90482 (88.3 KB)  TX bytes:90482 (88.3 KB)


```
after few minutes I couldn't connect to internet and when I execute **ifconfig** I get :
```
eth0      Link encap:Ethernet  HWaddr 00:15:C5:17:2B:D8  
          inet6 addr: fe80::215:c5ff:fe17:2bd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17027033 (16.2 MB)  TX bytes:2822194 (2.6 MB)
          Interrupt:22 

eth0:avah Link encap:Ethernet  HWaddr 00:15:C5:17:2B:D8  
          inet addr:169.254.145.140  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:965 errors:0 dropped:0 overruns:0 frame:0
          TX packets:965 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89507 (87.4 KB)  TX bytes:89507 (87.4 KB)
```
who to resolve this problem

---

### Post by superprash2003 on 2008-05-02
do an ifdown and ifup again..

---

### Post by lemming465 on 2008-05-02
New to me; none of my ubuntu systems have ever done this to me.  The *eth0:avah* makes me think that something weird is going on with avahi-daemon.  What other kinds of systems are running off your router?
The *169.254.145.140* IP address is from the "zeroconf" automatic address range, and doesn't match your router, which is the direct cause of the problem.  The advice fom superprash2003 is good, except I have a nagging feeling you will just get the problem back a few minutes later.

If you don't actually need Bonjour-style apple multicast DNS support, you could perhaps improve the situation with *sudo apt-get remove avahi-daemon*

---

### Post by jackm on 2008-05-03
> **superprash2003 said:**
> do an ifdown and ifup again..

I tried this, the problem is resloved but after few minutes later the problem is back

> **lemming465 said:**
> , except I have a nagging feeling you will just get the problem back a few minutes later.

it is true
> **lemming465 said:**
> 
If you don't actually need Bonjour-style apple multicast DNS support, you could perhaps improve the situation with *sudo apt-get remove avahi-daemon*
is it possible to stop disbale avahi-daomon with out remove it ?
I tried the following command , but the problem isn't resolved 
```
sudo /etc/init.d/avahi-daemon stop
```

---

### Post by stream303 on 2008-05-03
Could it be that your ethernet controller is entering a power-save mode as directed by the bios?

I've heard of this happening before and disabling power-management for the ethernet card in bios can cure it sometimes.

---

### Post by lemming465 on 2008-05-03
> ss it possible to stop disbale avahi-daomon with out remove it ?

Of course.  The likely thing to try would be stop avahi-daemon and then bounce the networks, e.g.```
sudo rm /etc/rc2.d/S18avahi-daemon
sudo /etc/init.d/networking restart
```

---

### Post by jackm on 2008-05-03
thanx lemming465 :)

---

