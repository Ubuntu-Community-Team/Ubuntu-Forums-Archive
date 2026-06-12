---
title: "Can't find Network address"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by Johnmacey on 2008-05-23
My IBM ThinkCentre, with Win XP Pro, & FireFox, on ATT"s DSL, works fine. I'm using Windows to send this Thread.  
I Used Wubi 7.04 to install Ubantu, and upgraded twice, now having ver.8.04.  
When I reboot to Ubantu, and click on Firefox, I get this error message: "Requesting network address from the wired network"
The broadband service arrives into a Westel modem (Supplied by BellSouth = now ATT), from there to a Belkin router, and from there to 3 computers.  The other 2 work just fine.
Can someone tell me what to do?  Please and thank you
johnmacey

---

### Post by mapes12 on 2008-05-23
Did the connection work with 7.04?

Do you have a wired or wireless connection?

---

### Post by Johnmacey on 2008-05-26
Yes the connection has been working. It is a wired connction

---

### Post by mapes12 on 2008-05-26
What output do you get from Terminal commands:

```
ifconfig

```
```
sudo dhclient
```

---

### Post by systat on 2009-01-06
I keep getting similar error, last night my WLAN worked, everything was perfect, and today when I woke up, and turn on laptop, I keep getting message no connection, even though, I could see my WLAN network, on list, and it's signal was fine.

I tried couple of times to connect, and the connecting icon was only showing lower blinking green light, while there was nothing on blinking on upper green light.
And after couple of blinks,I get no network connection.
:(

When I try to join WLAN, message on icon is Attempting to Join SpeedTouchDC3987.
And after some time, no network connection also.

I tried to connect to wired network, because I knew that worked every time when I installed Ubuntu, and needed to download necessary files to setup WLAN, but there same problem.

Requesting Network Address from Wired netwok message.
That message was there for 5 minutes, and tehre was connecting icon, lower green light was blinking, and so I decided to quit, I connected network cable back to my Windows XP desktop computer, and write this.

WLAN also works on my other laptop that is powered by Windows XP, so there must be some problem with my laptop





laptop@vampire:~$ sudo dhclient
[sudo] password for laptop: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Listening on LPF/wlan1/00:1a:73:6c:4c:b6
Sending on   LPF/wlan1/00:1a:73:6c:4c:b6
Listening on LPF/eth0/00:1a:4b:5e:2e:fe
Sending on   LPF/eth0/00:1a:4b:5e:2e:fe
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
laptop@vampire:~$ 



laptop@vampire:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4b:5e:2e:fe  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4382 (4.2 KB)  TX bytes:3060 (2.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14600 (14.2 KB)  TX bytes:14600 (14.2 KB)

wlan1     Link encap:Ethernet  HWaddr 00:1a:73:6c:4c:b6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5797 (5.6 KB)  TX bytes:8148 (7.9 KB)
          Interrupt:18 Memory:c8000000-c8004000

---

