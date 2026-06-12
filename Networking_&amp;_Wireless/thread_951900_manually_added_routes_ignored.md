---
title: "manually added routes ignored?"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by w9wi on 2008-10-18
Shoot.  Not finding anything relevant in the forums...

I have a new installation of 8.04.  I have dialup Internet access working on interface ppp0.  I also have an Ethernet interface so two Windows boxes can connect to the Ubuntu machine.  

I have not been able to get the Ethernet interface to work -- I cannot ping the Windows boxes or vice-versa.  (and of course, other network applications don't work either)  When I attempt to ping, I *do* see activity on the Ethernet LAN.  I do *not* see activity on the (external) modem on ppp0.  (although it's possible the ping packets are too short to see LED activity)

It appears to me as if the static route I added for Ethernet machines is being ignored:

```
w9wi@linux6:~/scripts$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
209.244.16.217  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     192.168.1.1     255.255.255.0   UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

```
w9wi@linux6:~/scripts$  ping 192.168.1.16
PING 192.168.1.16 (192.168.1.16) 56(84) bytes of data.
From 4.153.69.155 icmp_seq=1 Destination Host Unreachable
From 4.153.69.155 icmp_seq=2 Destination Host Unreachable
From 4.153.69.155 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.16 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4017ms
, pipe 3


```(4.153.69.155 is the IP address DHCP assigned to ppp0 when I dialed in...)

```
w9wi@linux6:~/scripts$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:18:a9:90:32  
          inet6 addr: fe80::230:18ff:fea9:9032/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24599 (24.0 KB)  TX bytes:12045 (11.7 KB)
          Interrupt:18 Base address:0xa000 
```

Note the "inet6" address.  The Network Administration Tool says the IP address of eth0 is 192.168.1.15 (which is what I want it to be!) but ifconfig seems to feel otherwise.    

So, I'm confused.  It looks as if the route I added for 192.168.1.0/ is being ignored.  Or it's grabbing the IP address from the ppp0 interface and transferring it to eth0.  What am I doing wrong??

I should say, the same hardware has run an earlier Ubuntu version (6.06?) on which this interface worked fine.

(how much trouble do I get in if I just copy /etc/network/* from the old 6.06 installation?!)

---

### Post by w9wi on 2008-10-18
Y'know, the easiest way to fix a problem is to post it on a web forum.....

It seems I needed to reboot...  The newly added route was appearing in the routing tables but it didn't actually work until after a restart.  

I'm pinging, Samba is up, and as soon as I get Apache installed I expect it to work.  The world is more or less good...

---

### Post by superprash2003 on 2008-10-19
presuming that you want to share an internet connection [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

