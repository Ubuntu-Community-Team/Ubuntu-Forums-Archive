---
title: "wired internet problem"
date: 2017-04-04
forum: Networking &amp; Wireless
---

### Post by santon834 on 2017-04-04
Hello,
I'm a Phd student at UCLA with a new Ubuntu 14.04 and Ethernet only Dell desktop. 
I have received internet specs from the department for connection but was unable to connect.
 The department tech support told me to google manuals online or install windows instead (?!).
 After going through many manuals I'm still unable to connect.  

The specs I have are:
IP
name (with the note "if the machine name does not match the IP address some services will not work properly")
Domain
Gateway
Subnet mask
DNS
Ports (I'm pretty sure the ports are physical ports inside the lab and are irrelevant for connection)

I have configured the network manager with the specs and changed the PC hostname.
I have also tried editing manually the internet connection ([COLOR=#000000][FONT=&quot]/etc/network/interfaces, [/FONT][/COLOR][COLOR=#000000][FONT=&quot]/etc/resolv.conf)[/FONT][/COLOR][COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]Ifconfig shows sent bytes but not received for eth0.
I can't ping the DNS "Destination Host unreachable"

Any help will be much appreciated.

---

### Post by ajgreeny on 2017-04-04
Hello santon834, and welcome to the forum.

Does your college use a proxy server connection?
Show us the full output of **ifconfig** please, as that may be more helpful than your own interpretation of what it showed.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by santon834 on 2017-04-06
Hi,
My department says there is no proxy server.
ifconfig output:

```
eth0   Linkencap:Ethernet  HWaddr 48:4d:7e:ce:26:06  
          inetaddr:164.67.194.145  Bcast:164.67.194.255  Mask:255.255.255.0
          inet6addr: fe80::56e6:373d:84f5:481f/64 Scope:Link
          UPBROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RXpackets:0 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:77350 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
          RX bytes:0(0.0 B)  TX bytes:4967191 (4.9 MB)
         Interrupt:16 Memory:f7200000-f7220000 


lo        Linkencap:Local Loopback  
          inetaddr:127.0.0.1  Mask:255.0.0.0
          inet6addr: ::1/128 Scope:Host
          UPLOOPBACK RUNNING  MTU:65536  Metric:1
          RXpackets:156065 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:156065 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1 
          RXbytes:13219253 (13.2 MB)  TX bytes:13219253 (13.2 MB)

```[COLOR=#000000]

[/COLOR]Thank you

---

### Post by santon834 on 2017-04-07
up

---

