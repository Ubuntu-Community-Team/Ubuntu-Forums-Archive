---
title: "eth0 dhcp no default gateway set"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by decrepit on 2007-02-17
This computer has fully working Fedora Core 4 and Windows XP.
Just installed Ubuntu 6.10 and having trouble connecting to the internet.

I have a siemens speedstream ADSL modem address 10.1.1.1 connected to the onboard NIC (supported by Ubuntu)
My ISP is dhcp. Their instructions for windows is to set eth0 to dhcp

Googled a fair bit, and tried a lot of stuff, but still haven't got there.
I've compared the working core4 with ubuntu, and concluded that for some reason ubuntu isn't setting the default gateway.
I've got eth0 selected in Admin, networking
Just to confuse things fedora calls the onboard NIC eth1 and ubuntu calls it eth0.

Here's the fedora results.
 
[root@core4 ~]# dhclient eth1
Internet Systems Consortium DHCP Client V3.0.2-RedHat
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:14:85:f4:2d:3d
Sending on   LPF/eth1/00:14:85:f4:2d:3d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 10.1.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.1.1.1
bound to 58.104.61.28 -- renewal in 50 seconds.
[root@core4 ~]#

[root@core4 ~]# ifconfig
eth1      Link encap:Ethernet  HWaddr 00:14:85:F4:2D:3D
          inet addr:58.104.61.28  Bcast:58.104.61.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fef4:2d3d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6255190 (5.9 MiB)  TX bytes:1457640 (1.3 MiB)
          Interrupt:193 Base address:0xa800

[root@core4 ~]# ip route show
211.31.137.131 dev eth1  scope link
58.104.61.0/24 dev eth1  proto kernel  scope link  src 58.104.61.28
169.254.0.0/16 dev eth1  scope link
default via 211.31.137.131 dev eth1
[root@core4 ~]#

PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data.
64 bytes from 10.1.1.1: icmp_seq=0 ttl=64 time=0.273 ms
64 bytes from 10.1.1.1: icmp_seq=1 ttl=64 time=0.252 ms
64 bytes from 10.1.1.1: icmp_seq=2 ttl=64 time=0.253 ms

--- 10.1.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2008ms
rtt min/avg/max/mdev = 0.252/0.259/0.273/0.016 ms, pipe 2
[root@core4 mike]# su -

[root@core4 ~]# ping -c 3 211.31.137.131
PING 211.31.137.131 (211.31.137.131) 56(84) bytes of data.
64 bytes from 211.31.137.131: icmp_seq=0 ttl=63 time=74.0 ms
64 bytes from 211.31.137.131: icmp_seq=1 ttl=63 time=75.7 ms
64 bytes from 211.31.137.131: icmp_seq=2 ttl=63 time=75.3 ms

--- 211.31.137.131 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 74.099/75.078/75.767/0.711 ms, pipe 2

And heres the same for ubuntu.
mike@ubu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:14:85:f4:2d:3d
Sending on   LPF/eth0/00:14:85:f4:2d:3d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.1.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.1.1.1
SIOCADDRT: Network is unreachable
bound to 58.104.61.28 -- renewal in 46 seconds.
mike@ubu:~$ 

mike@ubu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:85:F4:2D:3D  
          inet addr:58.104.61.28  Bcast:58.104.61.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fef4:2d3d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6167 (6.0 KiB)  TX bytes:3672 (3.5 KiB)
          Interrupt:225 Base address:0xa800 

mike@ubu:~$ sudo ip route show
Password:
58.104.61.0/24 dev eth0  proto kernel  scope link  src 58.104.61.28 
mike@ubu:~$ 

mike@ubu:~$ ping -c 3 10.1.1.1
connect: Network is unreachable

tried manually setting default gateway.

mike@ubu:~$ sudo route add default gw 211.31.137.131
SIOCADDRT: Network is unreachable

That didn't work either!

Anybody got any ides what's going on, or what I should try next, Please???

---

### Post by Floppyjoe on 2007-02-17
I searched a wee bit on Ubuntu forums and came up with this thread. I don't know if it will be of help to you though:

[http://www.ubuntuforums.org/showthread.php?t=309800&highlight=default+gateway](http://www.ubuntuforums.org/showthread.php?t=309800&highlight=default+gateway)

Floppyjoe

---

### Post by decrepit on 2007-02-17
Thanks Floppyjoe I missed that one.
Looks promising, only thing is the gateway address changes with every login, but I'll give it a try and report back.

---

### Post by decrepit on 2007-02-17
OK progress! 
did this.
mike@ubu:~$ sudo route add default dev eth0
mike@ubu:~$ ping 10.1.1.1
PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data.
64 bytes from 10.1.1.1: icmp_seq=1 ttl=64 time=0.247 ms
64 bytes from 10.1.1.1: icmp_seq=2 ttl=64 time=0.263 ms

that got me talking to the modem, but still couldn't bring in a url with the browser.

So then did this.
mike@ubu:~$ sudo route add default gw 211.31.137.130

Now I'm on line and writing this. BUT! the 211.31.137.130 is copied from core4 that I just logged out of, without turning off the modem.
What happens when  I  log in tomorrow??? Do I have to go into core4 first so I can get the new gateway address???
Going to try turning the modem off and see what hapens!

---

### Post by decrepit on 2007-02-17
As suspected that didn't work, but I hope I've found another solution.

I've gone to static configuration, called eth0 10.1.1.3 (just guessed this might work as modem is 10.1.1.1)

set gateway to 10.1.1.1

and used my isp's primary and secondary  DNS.

It's a mystery why Fedora and XP work with DHCP but ubuntu doesn't.

---

