---
title: "[SOLVED] No Wireless on 8.04"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by ubume2 on 2008-05-03
I've just installed Hardy on my wireless desktop. Have a 7050 Belkin usb device.  Desktop is a plain Dell Pentium4 i386

Either in roaming mode or not, I can't connect. Sometimes the network sees other networks out there. I have even tried broadcasting my essid. I used the sticky on how to set up wireless manually.

Here is what I get:

$ lshw -C network
name@name-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:4a:d2:f8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:17:3f:fe:f6:8a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g

sudo ifconfig eth0 down  ##no problem

name@name-desktop:~$ sudo dhclient -r eth0 
There is already a pid file /var/run/dhclient.pid with pid 134519072   ##dhclient.pid appears blank--not my essid
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:17:3f:fe:f6:8a
Sending on   LPF/eth1/00:17:3f:fe:f6:8a
Listening on LPF/eth0/00:11:11:4a:d2:f8
Sending on   LPF/eth0/00:11:11:4a:d2:f8
Sending on   Socket/fallback

sudo ifconfig eth0 up  ##no problem

name@name-desktop:~$ sudo iwconfig eth0 essid "XXXXXXXX"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth0 ; Operation not supported.


name@name-desktop:~$ sudo iwconfig eth0 key [number] ASCII KEY
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth0 ; Operation not supported.

name@name-desktop:~$ sudo iwconfig eth0 key open
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth0 ; Operation not supported.

name@name-desktop:~$ sudo iwconfig eth0 mode managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth0 ; Operation not supported.

name@name-desktop:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:11:4a:d2:f8
Sending on   LPF/eth0/00:11:11:4a:d2:f8
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I have read all of the posts and documents that I can find, but have not solved the problem. 

Please help.
Thank you

---

### Post by pro003 on 2008-05-03
when you type 

```
ifconfig
```


what you see?

---

### Post by ubume2 on 2008-05-03
Hi here is the result:

name@name-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:4a:d2:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:17:3f:fe:f6:8a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:332 dropped:2 overruns:0 frame:330
          TX packets:243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10374 (10.1 KB)

When first trying this I noticed /etc/network/interfaces only had

auto lo
iface lo inet loopback


I added 
auto eth0
iface eth0 inet dhcp

and got this:
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-key s:[my_ssid]
wireless-essid [myessid]

I commented them out later

Thanks for the help.

---

### Post by pro003 on 2008-05-03
seems like your internet connection goes through eth1

try

```
ifconfig eth0 down
```

then

```
ifconfig eth1 up
```

and set the roaming mode or choose manually your network.

do you use pass and user name?

---

### Post by ubume2 on 2008-05-03
will try it.

Hey Hey. It worked. I am connected. Have the wireless set up in a script now.

Thanks much.  How do I give you an official thank you?

---

### Post by pro003 on 2008-05-03
just click the star in the right corner of my reply...


but anyway glad you made it..  :guitar:

---

