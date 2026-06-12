---
title: "wireless connect to entranet server"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by linux4us on 2007-10-26
Hi, 

I have a DELL truemobile 1300 wireless card on my dell inspiron 4100 laptop, which runs Gusty. the wireless works fine except the connectivity to my desktop linux machine (Fedora 6).

yj@dajiang-laptop:~$ ssh -l yj abl
ssh: connect to host abl.ucsd.edu port 22: No route to host

yj@dajiang-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:10:C6:44:61:6C  
          inet addr:128.54.46.66  Bcast:128.54.47.255  Mask:255.255.252.0
          inet6 addr: fe80::210:c6ff:fe44:616c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:113052 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14974446 (14.2 MB)  TX bytes:1699921 (1.6 MB)
          Interrupt:11 Memory:2c000000-2c002000 

i suspect it is caused by the firewall setting on my laptop (default setting, after insallation, i didn't touch the security). but i don't know how to fix this. because in window xp on the same laptop, no such problem.

any ideas ?

thanks in advance.

yong

---

### Post by Lambert on 2007-10-27
explain your set up a little more. How your laptop is connected to internet, to desktop, how desktop is connected etc..

eth1 is showing a public address belonging to the university so I'm guessing all your network traffic is going to their router. The "no route" doesn't look like a firewall problem to me, more of when the packet gets to the university router, it doesn't have a path to your desktop to forward the traffic.

What is the ip address on your desktop?

---

### Post by linux4us on 2007-10-29
thanks for your reply.
my laptop connected to internet via school wireless server (DHCP), 
and my Desktop via static ip address which is specific for the building i am at.
here is my desktop ip info:

yj@abl:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:F4:EC:7E  
          inet addr:137.110.124.37  Bcast:137.110.124.127  Mask:255.255.255.128
          inet6 addr: fe80::213:d4ff:fef4:ec7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2276062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1561274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:175514716 (167.3 MiB)  TX bytes:5664408289 (5.2 GiB)

maybe as you said, it caused by school router, not the setting on my linux box, however if i boot to my windows xp on the same laptop, it works fine. how can you explain that ?

yong

---

### Post by Lambert on 2007-10-29
Both computers are on different subnets. I'm not sure why winxp works and ubuntu doesn't.
> 
inet addr:128.54.46.66 

inet addr:137.110.124.37


EDIT: need to research more of what I suggested.

---

### Post by linux4us on 2007-10-29
interesting, after i booted to windows,and back to linux, it works. but i am not sure what's the problem.

yong

---

