---
title: "Access to Windows NTFS Files"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by kencoburn on 2007-11-17
I have installed ntfs-3g, and ntfs-config and can access my windows files on my dual boot (Linux and Windows XP) computer.  This computer is connected to a peer-to-peer network over an Ethernet link using a Netgear router/modem/firewall.  When booted into Windows XP I have no problem accessing files on the remote computer but when I boot into Linux I can see the Windows Network icon (Places/Network).  Clicking on this gives me an icon with my workgroup name but when then I get I try to access the Windows network I get a message stating: The folder contents could not be displayed".

I turned off ZoneAlarm but that made no difference.  I suspect that the problem lies with the firewall settings of my Netgear router/modem/firewall.  Can you help resolve this problem?:(

---

### Post by mellowd on 2007-11-17
I don't think its a physical network problem. If the computers can see each other when booted into windows then there is no problem with the setup of the router. Sounds more like a problem with the network settings in linux

---

### Post by kencoburn on 2007-11-17
Thanks, but I answered the questions posed during the installation of Ubuntu about my network so I don't know where to go from here.  

I am fairly new to Linux. How do I check my network settings and what do I need to add or change to be able to read the files on the remote computer?

---

### Post by mellowd on 2007-11-17
Are you able to get to the internet from the linux box? To check your current settings open up a terminal and type ifconfig

---

### Post by kencoburn on 2007-11-17
Yes - I can surf the internet via the Linux computer.  

When I entered ifconfig from the terminal program I got the following:

ken@ken-gateway:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:E8:13:E1:DB  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e8ff:fe13:e1db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39424006 (37.5 MB)  TX bytes:2324969 (2.2 MB)
          Interrupt:3 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ken@ken-gateway:~$

---

### Post by mellowd on 2007-11-17
Are you able to ping the windows machine from the terminal?

---

### Post by kencoburn on 2007-11-17
I ping'd 192.168.0.6 and got a response but I am not sure whether this is the remote computer or the router that is responding.  The response was (abbreviated)

ken@ken-gateway:~$ ping 192.168.0.6
PING 192.168.0.6 (192.168.0.6) 56(84) bytes of data.
64 bytes from 192.168.0.6: icmp_seq=1 ttl=64 time=0.148 ms
64 bytes from 192.168.0.6: icmp_seq=2 ttl=64 time=0.105 ms
64 bytes from 192.168.0.6: icmp_seq=3 ttl=64 time=0.106 ms
64 bytes from 192.168.0.6: icmp_seq=4 ttl=64 time=0.105 ms
64 bytes from 192.168.0.6: icmp_seq=20 ttl=64 time=0.120 ms
64 bytes from 192.168.0.6: icmp_seq=21 ttl=64 time=0.120 ms
64 bytes from 192.168.0.6: icmp_seq=22 ttl=64 time=0.117 ms
64 bytes from 192.168.0.6: icmp_seq=23 ttl=64 time=0.111 ms

--- 192.168.0.6 ping statistics ---
23 packets transmitted, 23 received, 0% packet loss, time 21996ms
rtt min/avg/max/mdev = 0.074/0.113/0.148/0.018 ms
ken@ken-gateway:~$

---

### Post by MaximusTG on 2007-11-17
I'm not exactly sure about this, but don't you need the "samba" package to browse windows shares?

---

### Post by mellowd on 2007-11-17
go to the windows machine and type ipconfig in the command prompt to see the ip address of that machine. if its 0.6 then you are pinging that machine for sure

---

### Post by kencoburn on 2007-11-18
I get the following response when doing an ipconfig on the remote Windows XP computer:

Ethernet Adapter Local Area Connection
   Windows IP Configuration
   Connection-Specific DNS Suffix       :
   IP Address                                        : 192.168.0.2
   Subnet Mask                                     : 255.255.255.0
   Default Gateway                              : 198.168.0.1

---

### Post by mellowd on 2007-11-18
open up a terminal and type 

```
traceroute google.com

```
that will show you exactly what your router is as it will be your gateway. I think 0.6. is your router

---

### Post by kencoburn on 2007-11-18
Sorry - the Default Gateway is 192.168.0.1 and not 198.168.0.1

---

