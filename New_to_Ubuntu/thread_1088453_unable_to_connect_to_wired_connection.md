---
title: "unable to connect to wired connection"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by mrholdem on 2009-03-06
I have just installed ubuntu 8.10 intrepid

I am unable to connect to the internet. The network appears as though it is connected, however I am unable to ping ubuntu.com  or the suggested ip 91.189.94.249

Please advise.

---

### Post by dzark on 2009-03-06
if you open up a terminal, what are the results of ```
ifconfig
```

---

### Post by mrholdem on 2009-03-06
eth0 Link encap:Ethernet HWaddr 00:04:23:29:23:80
     UP BROADCAST RUNNING MULTICAST MTU:64 Metric:1
     Rx packets:198 errors:0 dropped:0 overruns:0 frame:0
     Tx packets:19 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:14069 (14.0 kb) tx bytes :2820 (2.8 kb)

lo   Link encap: Local Loopback
     inet addr:127.0.0.1 Mask:255.0.0.0
     inet6 addr:  :: 1/128 scope:host
     up loopback running mtu:16436 metric:1
     rx packets:256 errors:0 dropped:0 overrruns:0 frame:0
     tx packets:256 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     rx bytes 16160 16.1 kb  tx bytes 16160 16.1kb

---

### Post by dzark on 2009-03-06
As you say, connected but not actually doing anything...

What are you connected to? A modem/router with a DHCP server? Static IPs?

If you rightclick on network manager icon, select 'wired network' then add, try adding an 'Automatic (DHCP)' connection..

---

### Post by mrholdem on 2009-03-06
I am connected to a router with dynamic ips

The router reports that the machine is connected:
Dhcp client list:

IP Address  	Host Name  	MAC Address
192.xxx.x.xx  	electro  	000423292380


i created a network with the default name of wired connection 1
it requests the information
then gives a disconnected message however is still shown in the router setup.

---

### Post by dzark on 2009-03-06
dhcp names stay in the server (in this case router) for quite a while ~1700seconds normally so that's not much of an indicator...

What does your /etc/network/interfaces look like?

---

### Post by mrholdem on 2009-03-06
auto lo
iface lo inet loopback

---

### Post by dzark on 2009-03-06
what about if we add the lines:

```
auto eth0
iface eth0 inet dhcp
```

and then restart networking with

```
sudo /etc/init.d/networking restart
```

---

### Post by mrholdem on 2009-03-06
"you do not have permissions necessary...."

---

### Post by mrholdem on 2009-03-06
Ok, I got it saved. still no connection. would you like the results of the restart?

SIOCSIFADDR: No buffer space available.
is this a clue?

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send packet: Message too long

no DHCPOFFERS recieved
No working leases in persistent database - sleeping

---

### Post by mrholdem on 2009-03-06
I found a flash drive. complete details:


 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:04:23:29:23:80
Sending on   LPF/eth0/00:04:23:29:23:80
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No buffer space available
Listening on LPF/eth0/00:04:23:29:23:80
Sending on   LPF/eth0/00:04:23:29:23:80
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Message too long
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: No such device
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
 * if-up.d/mountnfs[eth0]: waiting for interface eth0 before doing NFS mounts
                                                                         [ OK ]

---

### Post by dzark on 2009-03-06
this looks pretty similar to what your having right now... 

[http://ubuntuforums.org/archive/index.php/t-1035031.html](http://ubuntuforums.org/archive/index.php/t-1035031.html)

---

### Post by mrholdem on 2009-03-06
thanks dzark.

I was able to fix it with a combonation of that post and this one:
[http://ubuntuforums.org/showthread.php?t=1029575](http://ubuntuforums.org/showthread.php?t=1029575)

I appreciate your time!!!

---

