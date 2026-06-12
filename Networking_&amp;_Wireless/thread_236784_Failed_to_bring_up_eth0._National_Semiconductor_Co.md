---
title: "Failed to bring up eth0. National Semiconductor Corporation DP83815"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by mazdam on 2006-08-15
Hello,

I already install 6.06 and have problem with properly configure network interface. Everything looks fine but I always receive network is unreachable message. Maybe somebody have the same problem with National Semiconductor Corporation DP83815 card I think that this is card problem???
I also download and insmod lan driver for kernel 2.6 and but it didn’t help…
 

sudo ifconfig -a  
eth0      Link encap:Ethernet  HWaddr 00:0B:CD:54:63:18  
          inet addr:80.48.123.XXX  Bcast:80.48.123.255  Mask:255.255.255.128
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1406063 (1.3 MiB)  TX bytes:84 (84.0 b)
          Interrupt:10 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

sudo lspci -v |grep Eth

0000:00:12.0 Ethernet controller: National Semiconductor 
Corporation DP83815 (MacPhyter) Ethernet Controller

/etc/network/interfaces

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 80.48.123.132
netmask 255.255.255.128
gateway 80.51.10.129

auto eth1
iface eth1 inet static
address 80.48.123.132
netmask 255.255.255.128
gateway 80.51.10.129

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


BR,

MM

---

### Post by nephish on 2006-08-15
you have two interfaces (eth0 and eth1) pointing to the same ip address. Is there a reason for that ? 
Are you trying to get connected by dhcp ? static ip ? DSL. 
looks like static. 
please copy what you have in /etc/network/interfaces to the forum. 
i don't, right now anyway, think anything is wrong with your ethernet card.
You only have one in there, right?

---

### Post by mazdam on 2006-08-15
I have only one Ethernet card, the reason that in /etc/network/interfaces you can see also eth1 is that I just for testing connect my Motorola modem by USB (is normal connect by LAN), nothing happened.
On this time only eth0 is up.

BR,

MM

---

### Post by nephish on 2006-08-15
can you ping your gateway ?
can you ping another computer by ip address?

print out your lsmod to see if a driver was loaded for your eth0

---

### Post by mazdam on 2006-08-15
Hello,

lsmod:
root@asiami-laptop:/media/sda1# lsmod |grep mac
macphy                 42256  0

ping gateway:

root@asiami-laptop:/media/sda1# ping 80.51.10.129
connect: Network is unreachable

ping another:
root@asiami-laptop:/media/sda1# ping 80.48.123.131
PING 80.48.123.131 (80.48.123.131) 56(84) bytes of data.
From 80.48.123.132 icmp_seq=2 Destination Host Unreachable
From 80.48.123.132 icmp_seq=3 Destination Host Unreachable
From 80.48.123.132 icmp_seq=4 Destination Host Unreachable
From 80.48.123.132 icmp_seq=6 Destination Host Unreachable
From 80.48.123.132 icmp_seq=7 Destination Host Unreachable
From 80.48.123.132 icmp_seq=8 Destination Host Unreachable

--- 80.48.123.131 ping statistics ---
9 packets transmitted, 0 received, +6 errors, 100% packet loss, time 8000ms
, pipe 3
root@asiami-laptop:/media/sda1# ping 80.48.123.130
PING 80.48.123.130 (80.48.123.130) 56(84) bytes of data.

--- 80.48.123.130 ping statistics ---
15 packets transmitted, 0 received, 100% packet loss, time 13997ms

/etc/init.d/networking restart:

 * Reconfiguring network interfaces...                                                                                                        SIOCADDRT: Network is unreachable
Failed to bring up eth0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                          
BR,

MM

---

