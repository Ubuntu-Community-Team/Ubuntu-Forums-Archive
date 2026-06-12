---
title: "Annoying Problem - Cannot Connect to Router Admin"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by Catsworth on 2007-02-10
Hi Guys,

I have a somewhat unusual problem, and I'm hoping it's going to be simple to solve.

Ok, here's what we have so far:

1.  I'm using Ubuntu 6.10
2.  My laptop has wireless and ethernet connections
3.  I'm using a Linksys WAG354G wireless modem/router
4.  I am using Firefox as my browser

The laptop establishes a connection to the router ok with either the ethernet or the wireless connection, and I can access the web with either connection.

In order to access the router's Admin control panel I type 192.168.1.1

When I'm connected via wireless this brings up the router's control panel, when connected via ethernet I get an error telling me that there was a problem loading the page (like the old 404 error from Windows).

I can ping the router from the wireless connection, but when I try from the ethernet connection I get a message stating that the destination host is unreachable.

Here's the output from *ifconfig*:

```
eth0      Link encap:Ethernet  HWaddr 00:02:3F:18:9C:6D  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fe18:9c6d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3383616 (3.2 MiB)  TX bytes:377410 (368.5 KiB)
          Interrupt:217 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:24:0B:1E  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe24:b1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3000 errors:1 dropped:1 overruns:0 frame:0
          TX packets:2780 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2096381 (1.9 MiB)  TX bytes:666179 (650.5 KiB)
          Interrupt:225 Base address:0xa000 Memory:d0000000-d0000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4748 (4.6 KiB)  TX bytes:4748 (4.6 KiB)
```

I've reset the router to the factory defaults, and then tried rebooting the laptop and connecting via ethernet using DHCP but that didn't work - this leads me to suspect that it's not something wrong on the router end but a misconfiguration somewhere in Ubuntu.

Can anybody give me any ideas what might be wrong here?

Thanks.

---

### Post by jml on 2007-02-10
My first thought is that your ethernet connection on the laptop is faulty.  Other than for Admin work,  can you access the network, surf the internet via the ethernet port?  If yes, then I agree it may be a configuration problem either in Ubuntu, or the wireless device.  If no, then  if you have a dual boot system, try connecting to the device via the ethernet card in Windows.  If it works, then I agree it may be a configuration problem.  Other things to consider, Ethernet cables do not take physical strain well.  Try using another cable and see if it works.  Also, if your wireless modem router has more than one RJ45 jack to connect to, try plugging your cable into a different one.

Joe

---

### Post by Catsworth on 2007-02-10
Hi, 

Thanks for your input.

When plugged in via Ethernet I can access Internet, email, and other services without any problems.  In fact, the _only_ thing I can't do is get to the router's admin control panel.

---

### Post by mshirey8 on 2007-02-10
Have you tried accessing from a different computer and/or with a different browser?

---

