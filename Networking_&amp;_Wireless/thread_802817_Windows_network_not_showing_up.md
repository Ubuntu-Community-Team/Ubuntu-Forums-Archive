---
title: "Windows network not showing up?"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by m0u53m4t on 2008-05-21
Under the "Windows Network" section I only have "Workgroup" and under that is only my machine.

I haven't configured the network at all, it all just worked and connected to the internet when I installed ubuntu. Any ideas?

---

### Post by superprash2003 on 2008-05-21
are you able to ping your windows computers?

---

### Post by Iowan on 2008-05-21
Check post#4 [here]("http://ubuntuforums.org/showthread.php?t=796106"). I just built a LAMPS (that's with Samba) server at work and I'm having similar problems.

---

### Post by m0u53m4t on 2008-05-22
> **superprash2003 said:**
> are you able to ping your windows computers?

Nope. Pinging their IP addresses just times out...

---

### Post by superprash2003 on 2008-05-22
ok theres the problem.. first you need to get that sorted out.. could you post ifconfig output from terminal of your ubuntu pc.. and also a ipconfig output from command prompt of a windows pc..

---

### Post by m0u53m4t on 2008-05-22
Just to explain my setup, I have 2 ethernet cards, my primary one which is connected to the house network and with an internet connection, then my other one plugged straight into a seperate modem because on vista if one connection dies it would switch to the other.

```
eth0      Link encap:Ethernet  HWaddr 00:0c:76:17:b7:ae  
          inet addr:82.11.253.26  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::20c:76ff:fe17:b7ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78647 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66641282 (63.5 MB)  TX bytes:10142504 (9.6 MB)
          Interrupt:20 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:50:8d:ef:1a:7d  
          inet6 addr: fe80::250:8dff:feef:1a7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2024323 (1.9 MB)  TX bytes:468 (468.0 B)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:308840 (301.6 KB)  TX bytes:308840 (301.6 KB)

```

Windows machine:
```
Connection-specific DNS suffix  .  :
IP Address  .  .  .  .  . : 192.168.1.114
Subnet Mask  .  .  .  . : 255.255.255.0
Default Gateway  .  .  . : 192.168.1.1
```


Edit:

I just unplugged the direct connection into the modem and tried smb://192.168.1.114/ and it's showing me the folders. 

Places>Network>Windows Network still shows nothing though

Edit2: 

When I scan the SMB network with the add a new printer thing it shows about 3/4 of the computers in the network, but only 2 of the 3 groups (Workgroup and JThorne but not diversions) and the pc with the printer is under the diversions group >__>

---

### Post by Iowan on 2008-05-22
You might enable the machine as either WINS server or Domain Master Browser.

---

