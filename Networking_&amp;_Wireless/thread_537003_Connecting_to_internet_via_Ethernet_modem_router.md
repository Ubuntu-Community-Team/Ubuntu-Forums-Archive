---
title: "Connecting to internet via Ethernet modem router"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by nihilio on 2007-08-28
Hello, I just installed Ubuntu 7.04 i386 on my PC and I have trouble connecting to the internet by the USRobotics 9107 modem-router I have.
The PC is connected via a PCI Ethernet card, Netgear's FA311.  I have set the internet connection both to DHCP (which gave me an adress totally irrelevant to the IP of the router) and the static IP suggested by my provider, I disabled IPv6, yet the computer still does not connect to the internet and it's browser fails to comunicate with the router.
On Netstat-ing the routing table information, what comes up is:
Dest                      |Gateway            |Netmask             |Interface
192.168.1.0         |0.0.0.0              |255.255.255.0   |eth0
169.254.0.0         |0.0.0.0              |255.255.0.0       |eth0
0.0.0.0                 |192.168.1.1      |0.0.0.0               |eth0

PC LAN IP: 192.168.1.3
Router IP:  192.168.1.1

Any idea on what may be wrong?

---

### Post by lloyd_b on 2007-08-28
Here are some tests to try and diagnose the problem.  In a terminal window:
```
ping -c 5 192.168.1.1
```
If you don't get any response to this, then you have a problem with the connection to your router.  Since you are getting your IP address and routing info from that router, I'd be very surprised if that fails, but it never hurts to double-check.

If that works:
```
ping -c 5 216.239.32.10
```
(that's a google.com IP address)
If it doesn't respond to that, but does respond to the previous test, then the issue is most likely between your modem/router and the internet.

Finally:
```
ping -c 5 www.google.com
```
If the first two tests succeed, but the third fails, then you have a problem with DNS (the service that translates names to IP addresses).  

Please post the results of these tests - they'll get us started on diagnosing things.  In addition - could you post the results of running the "ifconfig" command in a terminal, along with the contents of the file "/etc/resolv.conf"?

Lloyd B.

---

### Post by nihilio on 2007-08-29
Here you are:
mihalis@mihalis-desktop:~$ ping -c 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.3 icmp_seq=1 Destination Host Unreachable
From 192.168.1.3 icmp_seq=4 Destination Host Unreachable
From 192.168.1.3 icmp_seq=5 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4000ms
, pipe 2
------------
mihalis@mihalis-desktop:~$ ping -c 5 216.239.32.10
PING 216.239.32.10 (216.239.32.10) 56(84) bytes of data.
From 192.168.1.3 icmp_seq=3 Destination Host Unreachable
From 192.168.1.3 icmp_seq=4 Destination Host Unreachable
From 192.168.1.3 icmp_seq=5 Destination Host Unreachable

--- 216.239.32.10 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4016ms
, pipe 2
--------------
mihalis@mihalis-desktop:~$ ping -c 5 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
--------------
mihalis@mihalis-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:2F:2B:9C:91  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:10 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29462 (28.7 KiB)  TX bytes:29462 (28.7 KiB)
----------

---

### Post by lloyd_b on 2007-08-29
From your responses, it doesn't look like the computer is communicating with the router at all. 

I'm *assuming* (please correct me if I'm wrong) that this is with the machine configured with a static IP address (not DHCP).

If so - could you reset the computer for DHCP, reboot, and then post the results of the following commands:
```
ifconfig
route -n
```

What this sounds like is that the router is *not* configured to respond as 192.168.1.1.  The question is, what *is* it configured to respond as.  Hopefully, the DHCP info will provide a clue.

Lloyd B.

---

### Post by will71110 on 2007-08-29
Looks like you are recieving errors.  Check your LAN cable.  Try a different one if you have it.

---

### Post by nihilio on 2007-08-29
> **lloyd_b said:**
> From your responses, it doesn't look like the computer is communicating with the router at all. 

I'm *assuming* (please correct me if I'm wrong) that this is with the machine configured with a static IP address (not DHCP).

If so - could you reset the computer for DHCP, reboot, and then post the results of the following commands:
```
ifconfig
route -n
```

What this sounds like is that the router is *not* configured to respond as 192.168.1.1.  The question is, what *is* it configured to respond as.  Hopefully, the DHCP info will provide a clue.

Lloyd B.

The computer was set to static. The router responds to 192.168.1.1 for my windows XP PC connected to it. Nevertheless, I reseted the PC to DHCP, switched the cables (that means the cable the linux PC used is working for the windows system) and the results are that the system cannot even see the wired connection...

EDIT: A cold reboot later and it sees the network.
Here are the results:
mihalis@mihalis-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:2F:2B:9C:91  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:3 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe000 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:2F:2B:9C:91  
          inet addr:169.254.6.64  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4708 (4.5 KiB)  TX bytes:4708 (4.5 KiB)

mihalis@mihalis-desktop:~$ route -n
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

---

### Post by will71110 on 2007-08-29
> eth0      Link encap:Ethernet  HWaddr 00:1B:2F:2B:9C:91  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:3 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe000 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:2F:2B:9C:91  
          inet addr:169.254.6.64  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xe000 

Your computer is not getting DHCP according to this. This IP you have is a zero config IP.  You might have access to your internal network do you wont get out to the internet.  Do you have access to configure your router?

---

### Post by nihilio on 2007-08-29
> **will71110 said:**
> Your computer is not getting DHCP according to this. This IP you have is a zero config IP.  You might have access to your internal network do you wont get out to the internet.  Do you have access to configure your router?

Only from the WinXP PC, the linux one doesn't connect to the router (and the DHCP settings on the router are on, but I'll probably check them on the Win PC too - edit: works just fine).
More likely the problem lies in the network cark. Maybe I should go out and buy another one.

---

### Post by will71110 on 2007-08-29
Try reinstalling dhcp3-client using the synaptic package manger then reboot.

---

### Post by nihilio on 2007-08-29
Couldn't re-install DHCP-client 3. Trying to find a way to uninstal the original version then try again.

---

### Post by nihilio on 2007-08-29
Finaly it worked.
I reinstalled the OS, booted the PC while connected to the net, installed DHCP client and it finally worked. Must have forgotten something the first time around...
Thanks everyone for the help.

---

