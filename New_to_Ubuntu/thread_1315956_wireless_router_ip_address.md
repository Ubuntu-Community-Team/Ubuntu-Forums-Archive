---
title: "wireless router ip address"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by lucypeters on 2009-11-05
I am using di 624 wireless router and able to go online when the laptop is wired to the wireless router. I am able to go to the [http://192.168.0.1/](http://192.168.0.1/) setup page. But when unplug the cable from the laptop, wicd manager was unable to connect to go online. 

Do you know how to fix it?

Lucy

---

### Post by yeats on 2009-11-05
Hi Lucy,

Do you know what model wireless card you have?  From what I'm seeing here on the forums, there seems to be a problem with Broadcom cards not working automatically.

---

### Post by lucypeters on 2009-11-05
I don't know what model of my wireless card because I am using a laptop. 
ping -n 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=127 time=0.400 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=127 time=0.389 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=127 time=0.392 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=127 time=0.399 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=127 time=0.409 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=127 time=0.405 ms
^C
--- 192.168.0.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4999ms
rtt min/avg/max/mdev = 0.389/0.399/0.409/0.006 ms


traceroute -n 80.87.128.36
traceroute to 80.87.128.36 (80.87.128.36), 30 hops max, 60 byte packets
 1  192.168.0.1  0.345 ms  0.344 ms  0.321 ms
 2  10.219.60.1  47.581 ms  47.570 ms  49.265 ms
 3  81.100.0.61  24.634 ms  24.689 ms  24.668 ms
 4  81.100.0.69  24.655 ms * *
 5  212.43.162.57  25.819 ms  25.810 ms  25.569 ms
 6  213.105.174.230  25.725 ms  25.574 ms  25.804 ms
 7  213.105.172.137  60.424 ms  45.305 ms  45.097 ms
 8  213.152.245.49  50.740 ms  50.755 ms  59.593 ms
 9  64.125.28.197  65.189 ms  65.229 ms  65.214 ms
10  213.152.252.220  65.675 ms  66.144 ms  45.754 ms
11  80.87.128.36  54.853 ms  52.781 ms  50.290 ms

I hope the above information helps.

Lucy

---

### Post by lucypeters on 2009-11-05
My wireless card model are as follows:

eth0      Link encap:Ethernet  HWaddr 00:00:f0:71:c3:41  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:f0ff:fe71:c341/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1904151 (1.9 MB)  TX bytes:309161 (309.1 KB)
          Interrupt:10 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:1e:de:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0x6000 Memory:d0002000-d0002fff

---

### Post by yeats on 2009-11-05
If you can, type this at a terminal:

```
lspci
```

This will list your hardware, as Ubuntu sees it.  You can get more specific information by adding a -v or -vv to the end to make the output more _v_erbose.  You should see your card model listed in the output.

It *does* look like your wireless card is being picked up though (eth1 is almost certainly your wireless card).  You can run this command at a terminal to try and "manually" connect to your network (after unplugging from the wired network):

```
sudo dhclient eth1
```

see if you can post the output here and we can troubleshoot that.

---

### Post by lucypeters on 2009-11-06
lspci


02:05.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

02:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)



sudo dhclient eth1

There is already a pid file /var/run/dhclient.pid with pid 8107

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.1.1

Copyright 2004-2008 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth1/00:0e:35:1e:de:f8

Sending on   LPF/eth1/00:0e:35:1e:de:f8

Sending on   Socket/fallback

DHCPREQUEST of 192.168.0.104 on eth1 to 255.255.255.255 port 67

DHCPREQUEST of 192.168.0.104 on eth1 to 255.255.255.255 port 67

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5

No DHCPOFFERS received.

Trying recorded lease 192.168.0.104

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.



--- 192.168.0.1 ping statistics ---

1 packets transmitted, 1 received, 0% packet loss, time 0ms

rtt min/avg/max/mdev = 0.397/0.397/0.397/0.000 ms

bound: immediate renewal.

DHCPREQUEST of 192.168.0.104 on eth1 to 192.168.0.1 port 67


Please let me know if you need more info.

---

### Post by yeats on 2009-11-06
As I suspected, your wireless card is detected:

> 02:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

but your router is not granting an IP.  Can you go to your router's setup interface and see if there are any logs to view?

---

### Post by lucypeters on 2009-11-06
page 1 of 20
Time 	Message 	Source 	Destination 	Note
Apr/04/2002 06:04:52 	DHCP lease IP 192.168.0.103 to laptop			00-00-f0-71-c3-41
Apr/04/2002 06:04:40 	DHCP lease IP 192.168.0.103 to laptop			00-00-f0-71-c3-41
Apr/04/2002 00:35:21 	DHCP Request			86.1.111.198
Apr/03/2002 19:46:41 	DHCP release IP 192.168.0.103			00-00-f0-71-c3-41
Apr/03/2002 19:27:05 	DHCP lease IP 192.168.0.103 to laptop			00-00-f0-71-c3-41
Apr/03/2002 19:26:53 	DHCP lease IP 192.168.0.103 to laptop			00-00-f0-71-c3-41
Apr/03/2002 19:25:56 	Authenticating......			00-0e-35-1e-de-f8
Apr/03/2002 19:25:55 	Wireless PC connected			00-0e-35-1e-de-f8
Apr/03/2002 19:25:46 	Authenticating......			00-0e-35-1e-de-f8
Apr/03/2002 19:25:45 	Wireless PC connected			00-0e-35-1e-de-f8




page 20 of 20
Time 	Message 	Source 	Destination 	Note
Apr/02/2002 08:12:36 	Target IP(192.168.0.255), Target Port(138)			Packet Dropped
Apr/02/2002 08:12:36 	Spoof IP(192.168.0.103), Spoof Port(138)			
Apr/02/2002 08:12:36 	Spoof Attack fromd MAC(00-00-f0-71-c3-41) Detect,			
Apr/02/2002 08:09:51 	Target IP(192.168.0.255), Target Port(137)			Packet Dropped
Apr/02/2002 08:09:51 	Spoof IP(192.168.0.103), Spoof Port(137)			
Apr/02/2002 08:09:51 	Spoof Attack fromd MAC(00-00-f0-71-c3-41) Detect,			
Apr/02/2002 08:09:51 	Target IP(192.168.0.255), Target Port(137)			Packet Dropped
Apr/02/2002 08:09:51 	Spoof IP(192.168.0.103), Spoof Port(137)			
Apr/02/2002 08:09:51 	Spoof Attack fromd MAC(00-00-f0-71-c3-41) Detect,			

I got the above log from the [http://192.168.0.1/st_log.html](http://192.168.0.1/st_log.html)

What command can get the latest wireless log?

---

### Post by yeats on 2009-11-07
> Apr/04/2002

Looks like you need to update your modem's date! :-)

> Apr/02/2002 08:09:51 Spoof Attack fromd MAC(00-00-f0-71-c3-41) Detect,

This is your computer.  You know this from the "MAC(00-00-f0-71-c3-41)" part, because that matches this from ifconfig: "HWaddr 00:00:f0:71:c3:41."

Your router sees the same MAC address with a different hostname/host key behind it and is assuming that it's a "spoof" attempt.  I would investigate my router's manual about correcting this (and updating the date).

---

### Post by lucypeters on 2009-11-07
This is an updated log


page 1 of 20
Time
Message
Source
Destination
Note

Nov/07/2009 18:17:25 
DHCP lease IP 192.168.0.103 to laptop


00-00-f0-71-c3-41
Nov/07/2009 18:17:10 
DHCP lease IP 192.168.0.103 to laptop


00-00-f0-71-c3-41
Nov/07/2009 11:44:09 
DHCP release IP 192.168.0.103


00-00-f0-71-c3-41
Nov/07/2009 10:50:45 
DHCP lease IP 192.168.0.103 to laptop


00-00-f0-71-c3-41
Nov/07/2009 10:50:36 
DHCP lease IP 192.168.0.103 to laptop


00-00-f0-71-c3-41
Nov/07/2009 08:16:15 
DHCP Request success


86.1.111.198
Nov/07/2009 08:16:15 
DHCP Request


86.1.111.198
Nov/07/2009 08:16:14 
DHCP Request


86.1.111.198
Nov/07/2009 08:15:14 
DHCP Request


86.1.111.198
Nov/07/2009 08:14:12 
DHCP Request


86.1.111.198




page 20 of 20
Time
Message
Source
Destination
Note

Nov/04/2009 22:25:01 
Spoof Attack fromd MAC(00-00-f0-71-c3-41) Detect,



Nov/04/2009 22:25:01 
Target IP(192.168.0.255), Target Port(137)


Packet Dropped
Nov/04/2009 22:25:01 
Spoof IP(192.168.0.103), Spoof Port(137)



Nov/04/2009 22:25:01 
Spoof Attack fromd MAC(00-00-f0-71-c3-41) Detect,



Nov/04/2009 22:25:00 
Target IP(192.168.0.255), Target Port(137)


Packet Dropped
Nov/04/2009 22:25:00 
Spoof IP(192.168.0.103), Spoof Port(137)



Nov/04/2009 22:25:00 
Spoof Attack fromd MAC(00-00-f0-71-c3-41) Detect,



Nov/04/2009 22:23:52 
Target IP(192.168.0.255), Target Port(138)


Packet Dropped
Nov/04/2009 22:23:52 
Spoof IP(192.168.0.103), Spoof Port(138)



Lucy

---

### Post by yeats on 2009-11-07
Does there seem to be any way to fine-tune your router's security settings?

---

### Post by lucypeters on 2009-11-08
In [http://192.168.0.1/h_wireless.html](http://192.168.0.1/h_wireless.html) I can config the router's security. My Access Point config are as follows:

I am using Auto select channel and Super G without turbo.

I have disabled Extended Range Mode, WMM Function (Wireless Qos)and 802.11g Only Mode. 

I have enabled SSID Broadcast WPA Security in TKIP and PSK.

I use Dynamic IP Address and disabled Romote Management.

Lucy

---

### Post by yeats on 2009-11-08
Lucy,

I was just looking at the manual for your router (from [http://www.dlink.com/products/?tab=3&pid=DI-624&rev=DI-624](http://www.dlink.com/products/?tab=3&pid=DI-624&rev=DI-624)) and I *think* you may be able to fix this by creating a MAC filter that allows your Ubuntu installation through.  In your router's administration page, go to Advanced -> Filters -> MAC Filters, and see if you can make your router realize that your computer is not actually a spoof attack.  Another option, especially if you are not using Windows on that computer is to reset the router to factory settings (realize that this will mean you have to reconfigure it completely) then see if you can get it to grant you an IP address.

Chris

---

### Post by lucypeters on 2009-11-08
At the bottom of the MAC Filters page, there is an IP Filter list and the list is as follows:
TCP 20-21, TCP 80, TCP 443, UDP 53,TCP 25, TCP 110 and TCP 23

which one in the list should I delete ?

Lucy

---

### Post by yeats on 2009-11-08
I wouldn't actually delete those.  It looks like those are controlling access to particular default ports (80, 443) that you actually want to act the way they already do...

My hope is there is a way to define a rule that says "lucy-laptop with MAC address XX-XX-XX-XX should be able to get an IP from the DHCP server".

---

### Post by lucypeters on 2009-11-09
How can I find out the IP address from the DHCP server so it can go online ?

Lucy

---

### Post by yeats on 2009-11-09
I think your router is not going to grant you one, since it thinks your Ubuntu computer is a spoof attack.  I think you'll want to contact your router's tech support to see if you can set it up to grant an IP to more than one OS with the same MAC address.

Good luck with this.

Chris

---

### Post by lucypeters on 2009-11-11
I wish my router's tech support could help me because di 624's product's life was ended in August 2007 see [http://www.dlink.com/products/?pid=6](http://www.dlink.com/products/?pid=6) . I bought it because it was an award winning router and I thought it couldn't go wrong. 

I have switched to Static IP address and disabled DHCP but still no wireless connection.

Do you know how to turn the wireless router into a Bridge mode ?

Lucy

---

