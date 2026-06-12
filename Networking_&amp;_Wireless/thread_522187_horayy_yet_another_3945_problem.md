---
title: "horayy yet another 3945 problem"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by anfractuosities on 2007-08-10
My wireless has been working for months and then "all of a sudden" it will connect, with a fairly strong signal, but no data will be transmitted.  I can even ping the isp for some reason.  Im running fiesty and xp on an asus z96j.  any help would be graeat

thanks

---

### Post by noob12 on 2007-08-10
Was that a typo, or did you say you *can* ping the ISP?  If you can ping the ISP, it's probably working, and you have some other issue.  You'll need to elaborate.

---

### Post by anfractuosities on 2007-08-10
that is correct, i can ping.  But no browser, package manager, or any other program will connect to anything.
the connection is estabilished right when ubuntu finishes loading, the active connection information is all there.  when i use the network tools to ping the ip adress that i can see in the connection information box
 i get an average of .03 ms w/ 100% average. if you need any more info ill be happy to provide it.

tahnks

---

### Post by newdamage1 on 2007-08-10
Can you do a nslookup to yahoo, google and have it come back with an IP?


> **anfractuosities said:**
> that is correct, i can ping.  But no browser, package manager, or any other program will connect to anything.
the connection is estabilished right when ubuntu finishes loading, the active connection information is all there.  when i use the network tools to ping the ip adress that i can see in the connection information box
 i get an average of .03 ms w/ 100% average. if you need any more info ill be happy to provide it.

tahnks

---

### Post by anfractuosities on 2007-08-10
that is a negative. it will not ping a .com either

---

### Post by noob12 on 2007-08-10
Can you post the result of these
```

ifconfig -a

grep dhclient /var/log/syslog | tail -50

cat /etc/resolv.conf

```

and the output of a couple one of your successful router pings.

---

### Post by anfractuosities on 2007-08-10
ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:18:F3:85:77:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xac00 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:11:D6:CD  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe11:d6cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4409 (4.3 KiB)  TX bytes:5420 (5.2 KiB)
          Interrupt:17 Base address:0xe000 Memory:ff8ff000-ff8fffff 

eth0:avah Link encap:Ethernet  HWaddr 00:18:F3:85:77:35  
          inet addr:169.254.6.115  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)



grep


Aug 10 11:41:43 mymy-laptop dhclient: No DHCPOFFERS received.
Aug 10 11:41:43 mymy-laptop dhclient: No working leases in persistent database - sleeping.
Aug 10 11:41:46 mymy-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Aug 10 11:41:47 mymy-laptop dhclient: DHCPOFFER from 192.168.1.1
Aug 10 11:41:47 mymy-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Aug 10 11:41:47 mymy-laptop dhclient: DHCPACK from 192.168.1.1
Aug 10 11:41:47 mymy-laptop dhclient: bound to 192.168.1.101 -- renewal in 42917 seconds.
Aug 10 11:46:37 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 10 11:46:40 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 10 11:46:49 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Aug 10 11:47:02 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Aug 10 11:47:08 mymy-laptop dhclient: No DHCPOFFERS received.
Aug 10 11:47:08 mymy-laptop dhclient: No working leases in persistent database - sleeping.
Aug 10 11:52:38 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Aug 10 11:52:56 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Aug 10 11:53:05 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 10 11:53:09 mymy-laptop dhclient: No DHCPOFFERS received.
Aug 10 11:53:09 mymy-laptop dhclient: No working leases in persistent database - sleeping.
Aug 10 11:56:35 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Aug 10 11:56:38 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug 10 11:56:43 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug 10 11:56:50 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Aug 10 11:57:05 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Aug 10 11:57:05 mymy-laptop dhclient: No DHCPOFFERS received.
Aug 10 11:57:05 mymy-laptop dhclient: No working leases in persistent database - sleeping.
Aug 10 12:00:52 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug 10 12:00:57 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Aug 10 12:01:09 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Aug 10 12:01:23 mymy-laptop dhclient: No DHCPOFFERS received.
Aug 10 12:01:23 mymy-laptop dhclient: No working leases in persistent database - sleeping.
Aug 10 12:08:25 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug 10 12:08:31 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Aug 10 12:08:41 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Aug 10 12:08:55 mymy-laptop dhclient: No DHCPOFFERS received.
Aug 10 12:08:55 mymy-laptop dhclient: No working leases in persistent database - sleeping.
Aug 10 12:10:03 mymy-laptop dhclient: receive_packet failed on eth1: Network is down
Aug 10 12:10:58 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Aug 10 12:11:02 mymy-laptop dhclient: isc-dhclient-V3.0.4
Aug 10 12:11:06 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Aug 10 12:11:21 mymy-laptop dhclient: No DHCPOFFERS received.
Aug 10 12:11:21 mymy-laptop dhclient: No working leases in persistent database - sleeping.
Aug 10 12:11:25 mymy-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Aug 10 12:11:25 mymy-laptop dhclient: DHCPACK from 192.168.1.1
Aug 10 12:11:25 mymy-laptop dhclient: bound to 192.168.1.101 -- renewal in 40690 seconds.
Aug 10 12:16:42 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 10 12:16:46 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 10 12:16:50 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Aug 10 12:17:00 mymy-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Aug 10 12:17:13 mymy-laptop dhclient: No DHCPOFFERS received.
Aug 10 12:17:13 mymy-laptop dhclient: No working leases in persistent database - sleeping.



cat


# generated by NetworkManager, do not edit!

search tvc.chartermi.net


nameserver 24.247.24.53
nameserver 24.247.15.53


ping---------------

ping 192.168.1.101
min .02ms
ave .03ms
max .03ms

packets :5
recived 5
100%


and if i try to ping google, network tools freezes up. the ping button doesnt even change into the stop button..??

---

### Post by noob12 on 2007-08-10
Is your wireless on eth0 or eth1?   Can you run an **iwconfig** to check?

The 101 address is your own, not the router's.  However your box did communicate with the router at 192.168.1.1 to get the 101 address assigned to eth1, so if that's the wireless it's good.  They probably can talk.  

What happens when you ping your nameservers?  e.g.  **ping 24.247.24.53**

Can you show us the output of **route -n**?

---

### Post by anfractuosities on 2007-08-10
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:A7:9A:EE   
          Bit Rate:18 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/100  Signal level=-81 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0





no response on ping of 242472453


route -n


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0




thank you so much for all your help

---

### Post by noob12 on 2007-08-10
OK.  Please try these and let me know.
```

sudo /sbin/ifdown eth0
ping 192.168.1.1
ping 24.247.24.53
ping 209.131.36.158

```
The last is a yahoo / akamai IP.

---

### Post by anfractuosities on 2007-08-10
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5832
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:18:f3:85:77:35
Sending on   LPF/eth0/00:18:f3:85:77:35
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67



192.168.1.1

min 1.51
ave 4.16
max 5.27

100%

all others fail

---

### Post by noob12 on 2007-08-10
It appears to be your ISP or your router.  Traffic to your local router 192.186.1.1 is working.  Beyond that all of them failed.  What was the ISP address that you thought you could ping?

Do you have any other boxes on the local net that are connecting to the net?

---

### Post by anfractuosities on 2007-08-11
it was 192.168.1.101 . The wireless im connecting to is my neighbor's, who is on vacation.  So I can't ge to the router.  In a few weeks, Ill be able to see if there is a problem on their end.  Thanks for all your help. I really appreciate it.  

I love linux

---

