---
title: "Connected to network but no internet connection"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by dissonant on 2008-07-05
Hey all!
I just moved to a new apartment which has a DLink DI-634M router connected to a Motorlla SurfBoard cable modem. There are two computers connected to the router, one wired and the other wireless. Both computers running windows and having a working internet connection.

I have a IBM T60p laptop running Ubuntu 7.10.
Initially I tried connecting to the network through the wireless device. It seemed like I was connected to the network but I couldn't get reach any external host.

I decided to try using the wired connection first. Again, I was connected to the network but no internet connection. when I pinged 192.168.0.1 (the router address) I got an answer but when trying to connect in HTTP (or just telnet using port 80) I couldn't connect.

After some research on google and the forums I found out that after I run dhclient, I can access [http://192.168.0.1](http://192.168.0.1) but still I can't reach outside my network.
I also tried connecting directly to the modem but still no luck.

Here's the output of some commands that might help you figure out my problems. I ran these commands while connected by wire to the router. Thanks in advance!


sudo dhclient
```
There is already a pid file /var/run/dhclient.pid with pid 17553
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:02:25:58:8f
Sending on   LPF/eth1/00:13:02:25:58:8f
Listening on LPF/vmnet8/00:50:56:c0:00:08
Sending on   LPF/vmnet8/00:50:56:c0:00:08
Listening on LPF/vmnet1/00:50:56:c0:00:01
Sending on   LPF/vmnet1/00:50:56:c0:00:01
Listening on LPF/eth0/00:15:58:28:ea:0b
Sending on   LPF/eth0/00:15:58:28:ea:0b
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on vmnet1 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.145 -- renewal in 295555 seconds.
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:15:58:28:EA:0B  
          inet addr:192.168.0.145  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe28:ea0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2358 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:364324 (355.7 KB)  TX bytes:245071 (239.3 KB)
          Base address:0x3000 Memory:ee000000-ee020000 

eth1      Link encap:Ethernet  HWaddr 00:13:02:25:58:8F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:25 dropped:58821 overruns:0 frame:0
          TX packets:0 errors:0 dropped:18 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9425745 (8.9 MB)  TX bytes:9418058 (8.9 MB)
          Interrupt:22 Base address:0xe000 Memory:edf00000-edf00fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1768067 (1.6 MB)  TX bytes:1768067 (1.6 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.162.128  Bcast:192.168.162.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1059 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.0.128  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```


route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.162.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         192.168.0.2     0.0.0.0         UG    0      0        0 vmnet8
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by dissonant on 2008-07-05
Forgot to mention - 
1. I've been using this installation of Ubuntu for several months and I never encountered such problems.
2. Connecting other networks, wired and wireless, still works good..

---

### Post by superprash2003 on 2008-07-05
in the terminal type ping google.com and post output here..

---

### Post by dissonant on 2008-07-05
ping google.com
```
ping: unkown host google.com
```

nslookup google.com
```
;; connection timed out; no servers could be reached
```

---

### Post by dissonant on 2008-07-06
Have anyone encountered something similar? I've spent hours trying to fix it with no luck ...

---

### Post by DiGiTGOD on 2008-07-06
just a thought... I'm no guru... but I've had this problem for a while.

The problem I had is that the router was not working as a DNS to the pc's on the network.  In windoze I just set the ISP's DNSs'up in the Ip configuration...  and I can do the same on Kubuntu.  My problem is that I have to add them everytime I boot up.

to work out whether this is the problem... try pinging 72.14.207.99 which is one of Google's IPs.  If it works, it's just that the DNS's aren't working...

You could also look at the /etc/resolv.conf, but this will probably just say your routers' IP which is not much use...

Just thought I'd share my experience, if anyone can tell me how to do this automatically at boot it would be much appreciated...

---

### Post by DiGiTGOD on 2008-07-06
update... just found a way of doing it at startup if you need...

edit the file /etc/dhcp3/dhclient.conf

add the line 

```
prepend domain-name-servers <Address1>,<address2>;
```

This does the job for me...

hope it helps.

---

### Post by dissonant on 2008-07-06
Hey DiGiTDOG, thanks for your comment!
It seems like I have the same problem as I do get response when pinging Google IP directly. 
How did you solve this problem?
My /etc/resolv.conf:
```

search cable.rcn.com
nameserver 192.168.0.2

```

---

### Post by dissonant on 2008-07-06
Something really weird going on here. When I was pinging Google server directly it worked for a couple of times and then all of the sudden I get the following:
```

ping 72.14.207.99
From 192.168.0.128 icmp_seq=1 Destination Host Unreachable

```

It's like I don't get the response from the IP I tried but from somewhere else.. I don't even know what 192.168.0.128 is...

---

### Post by superprash2003 on 2008-07-07
ok there might be some kinda conflict here.. try disabling or removing the vmnet adapters cause 192.168.0.128 is the ip of one of your vmnet adapters

---

