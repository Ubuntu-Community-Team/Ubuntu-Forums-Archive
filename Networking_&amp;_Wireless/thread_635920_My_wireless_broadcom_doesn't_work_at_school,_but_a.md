---
title: "My wireless broadcom doesn't work at school, but at home"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by torswin on 2007-12-09
Hello. I'm a not-so-proud owner of a Broadcom 43xx (not exactly sure which model, sorry), and I can't use Ubuntu at school (I'm dual-booting Ubuntu and Windows) because I can't use their wireless network.

Their network is a simple non-encrypted wireless network where the first page you get to is a page where you have to type in your username and password, you know. Anyway, I never get that far.

When I try to connect to it with Ubuntu it either won't connect at all (only one light in the network-manager lights, and after a while turns into the Network Unavailable icon), or it will connect for about a minute or two 'till it turns into the Network Unavailable icon. 

The times I get to connect to it, all pages result in "could not resolve the host" and I never get to type in my username and password. 

I have run ifconfig eth0 when I was conneted, which said:
torswin@Bishop:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:14:A5:F2:CA:4D  
          inet addr:10.250.130.87  Bcast:10.250.255.255  Mask:255.255.128.0
          inet6 addr: fe80::214:a5ff:fef2:ca4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:852 errors:0 dropped:396 overruns:0 frame:0
          TX packets:2032 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:639029 (624.0 KB)  TX bytes:153452 (149.8 KB)
          Interrupt:10

I really need to be able to access Internet at school, or I'll be forced to use Windows :( It works on every other wireless I've tried, and it works on Windows XP. Don't know why it wont work on Ubuntu :confused:

---

### Post by torswin on 2007-12-09
After a bit of looking around on Google I am pretty certain that I have a Broadcom 4311. The driver I am currently using is the one that I received through Restricted Drivers, and it works good on all networks but this one.

---

