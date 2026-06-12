---
title: "Ubuntu 6.10 Dual Boot Internet Connection Problem"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by aldrin_p on 2006-11-26
Hi,
 I am new to Ubuntu. I installed a dual boot windows 2000/Ubuntu 6.10 OS on my Desktop. My configuration has a DSL modem-connected to a Dlink Router-connected to two computers ( Dual PC1 & another PC with XP).
 Ubuntu, when configured to receive automatic ip does not work. DHCP discover finds no offers. So, I have set the ip configuration in Ubuntu as static. With the configuration I have, I am unable to ping my router or the other XP PC or access the internet. Please help. The following is my ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:50:8B:30:FF:13  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8bff:fe30:ff13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:18385 dropped:0 overruns:0 carrier:36760
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6905 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:636970 (622.0 KiB)  TX bytes:636970 (622.0 KiB)

I have configured the gateway ip to my router ip.

The output fro eth0 interface has Tx errors. Not sure why this error occurs. Also, the Router does not recognize the lan connection from the ubuntu PC. Everything works great, if booted with Windows. Thanks for your help.

---

### Post by foxmulder881 on 2006-11-27
Are you sure you have the IPs configured correctly in Ubuntu. Its most certainly not a hardware issue if it works in Windows.

---

### Post by aldrin_p on 2006-11-27
Hi,
 The ip's are all correct, but my ethernet is dead. My router doesn't see it. Ethernet comes back alive if booted with windows.

---

