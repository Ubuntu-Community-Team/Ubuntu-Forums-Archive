---
title: "Xircom Realport Ethernet 10/100 RE-100 does't autoconnect"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by naubusan on 2007-06-26
Hi,
So the problem is when I start my laptop there is no lan connection until I put manuallly ip 192.168.1.2 and ok
Then I put dhcp back and everything works until next restart...

---

### Post by naubusan on 2007-06-26
Noticed That It doesnt get IP on bootup. But when I disable connection and put it back on everything is ok.
Its an pcmcia card.
Havent found any solutions for that.

---

### Post by chili555 on 2007-06-26
How about letting us take a look at the output from two terminal commands:```
cat /etc/network/interfaces
ifconfig
```Thanks.

---

### Post by naubusan on 2007-06-26
auto lo
iface lo inet loopback



iface eth0 inet dhcp
address 192.168.1.2
netmask 255.255.255.0

auto eth0


and



ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:A4:7E:F8:33  
          inet addr:80.222.27.248  Bcast:80.222.31.255  Mask:255.255.240.0
          inet6 addr: fe80::210:a4ff:fe7e:f833/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:930466 (908.6 KiB)  TX bytes:194938 (190.3 KiB)
          Interrupt:3 Base address:0x300 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1464 (1.4 KiB)  TX bytes:1464 (1.4 KiB)

This is now when I have connection...:D

---

### Post by chili555 on 2007-06-26
This:```
iface eth0 inet dhcp
```says I will take any old IP address the DHCP server will give me. However, this:```
address 192.168.1.2
```says I want the static address 192.168.1.2, forget about DHCP.

Moreover, this:```
inet addr:80.222.27.248
```says I have an IP address and 192.168.x.x is NOT the right neighborhood. And the netmask entries, x.x.255.0 in *interfaces* and x.x.240.x in *iwconfig* conflict. I wonder where you got the 192.168.1.2 information. Are you behind a router or connected directly to a cable or DSL modem?

In any event, I would *sudo gedit /etc/network/interfaces* and make it look like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```Reboot and post back to let us know.

---

### Post by naubusan on 2007-06-26
Ok, not working.
I have  zyxel prestige adsl modem with gateway
And here is interfaces and ifconfig right after boot when nothing works..


> &#65279;# This file describes the network interfaces available on your system

# and how to activate them. For more information, see interfaces(5).



# The loopback network interface

auto lo

iface lo inet loopback



auto eth0

iface eth0 inet dhcp 















 ifconfig

eth0      Link encap:Ethernet  HWaddr 00:10:A4:7E:F8:33  

          inet6 addr: fe80::210:a4ff:fe7e:f833/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:8940 (8.7 KiB)

          Interrupt:3 Base address:0x300 



eth0:avah Link encap:Ethernet  HWaddr 00:10:A4:7E:F8:33  

          inet addr:169.254.7.178  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          Interrupt:3 Base address:0x300 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:53 errors:0 dropped:0 overruns:0 frame:0

          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:4950 (4.8 KiB)  TX bytes:4950 (4.8 KiB)






---

### Post by naubusan on 2007-06-26
Just guessing.. is this something what is making problems.
I don't have avahi on, but it doesn't make difference if it is on or off.

```
eth0:avah Link encap:Ethernet HWaddr 00:10:A4:7E:F8:33

inet addr:169.254.7.178 Bcast:169.254.255.255 Mask:255.255.0.0

UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

Interrupt:3 Base address:0x300 
```

---

### Post by chili555 on 2007-06-26
Avahi assigns a 169.254.x.x IP address when a DHCP server can't be found or doesn't respond. Please try:```
sudo ifdown eth0 && sudo ifup eth0
```Let us know if you get an actual IP address and we'll troubleshoot a bit more.

---

### Post by naubusan on 2007-06-27
Had to sleep a little :), and work also..

But that worked, I got an IP and connection.

```
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5053
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:10:a4:7e:f8:33
Sending on   LPF/eth0/00:10:a4:7e:f8:33
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 80.222.xx.xx port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:10:a4:7e:f8:33
Sending on   LPF/eth0/00:10:a4:7e:f8:33
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
ip length 335 disagrees with bytes received 339.
accepting packet with data after udp payload.
DHCPOFFER from 80.222.xx.xx
DHCPREQUEST on eth0 to 255.255.255.255 port 67
ip length 335 disagrees with bytes received 339.
accepting packet with data after udp payload.
DHCPACK from 80.222.xx.xx
bound to 80.222.xx.xxx -- renewal in 13019 seconds.
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon
   ...done.

```

---

### Post by naubusan on 2007-07-02
Still have this problem,that after bootup computer does't connect before resetting connection.
Any suggestions?

---

### Post by chili555 on 2007-07-02
Sorry for the delay in replying. This thing ought to start up practically before you take your finger off the power button.

This is a bit of a hack, but let's *gksudo gedit /etc/rc.local* to add the following, just above the line, *exit 0*```
ifdown eth0 && ifup eth0
```Save and close gedit. Reboot and let us know.

---

### Post by naubusan on 2007-07-05
Yep, that doesn't work either. First when I tested this ifup-ifdown thingy it worked, but after that I have been unsuccessful with it. Seems that it cannot fetch dns ips and address automatically. 
Laptop is friend of mine and I copied dns addresses manuallu from my desktop on the laptop.
When I returned machine I rermoved dns addresses, and now it won't find anything even if resetting connection.
Now I'm afraid that time is running out and I have to put xp on it:(

---

