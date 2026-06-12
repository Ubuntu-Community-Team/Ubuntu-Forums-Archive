---
title: "Ubuntu Live - Connection Established! Nothing in FF"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by korbennn on 2010-08-06
I dropped the wubi idea and want to test Ubuntu 10.04 x64 LIveCD
Started with the most obvious part - WiFi

I keyed in the necessary data, i.e. Ip, Subnet, Getaway, DNS 
In Network Tools 100% packets yet no www can be accessed thru FF :(

I also noticed that mac address here is different from what I've seen in Win7
I did try different DNS
4.2.2.1
8.8.8.8
8.8.4.4
No luck


I searched some threads and they advised on trying these commands
> 
ubuntu@ubuntu:~$ ping 4.2.2.1 -c3
connect: Network is unreachable
ubuntu@ubuntu:~$ ping 83.80.1.236
connect: Network is unreachable
ubuntu@ubuntu:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:24:be:79:5d:27 
inet6 addr: fe80::224:beff:fe79:5d27/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:4914 (4.9 KB)
Interrupt:16 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:488 errors:0 dropped:0 overruns:0 frame:0
TX packets:488 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:38144 (38.1 KB) TX bytes:38144 (38.1 KB)

wlan0 Link encap:Ethernet HWaddr 00:24:d6:10:18:7e 
inet addr:192.168.1.7 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::224:d6ff:fe10:187e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:49 errors:0 dropped:0 overruns:0 frame:0
TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:10051 (10.0 KB) TX bytes:14040 (14.0 KB)

ubuntu@ubuntu:~$

Any bright ideas? :popcorn:

Same with Mint 9 - connected, still no connection...


edit// as for changing the mac

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether xxxxxxx
sudo ifconfig eth0 promisc
sudo ifconfig eth0 up

as well as
sudo gedit /etc/network/interfaces

auto eth0
iface eth0 inet dhcp
hwaddress ether 01:02:03:04:05:06
sudo /etc/init.d/networking restart

the results are as follow:
> 
ubuntu@ubuntu:~$ sudo ifconfig eth0 hw ether 00-24-D6-10-18-7E
00-24-D6-10-18-7E: invalid ether address.
ubuntu@ubuntu:~$ sudo ifconfig eth0 down
ubuntu@ubuntu:~$ sudo ifconfig eth0 hw ether 00:246:10:18:7E
ubuntu@ubuntu:~$ sudo ifconfig eth0 promisc
ubuntu@ubuntu:~$ sudo ifconfig eth0 up
ubuntu@ubuntu:~$ sudo gedit /etc/network/interfaces
ubuntu@ubuntu:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:24:d6:10:18:7e
Sending on LPF/eth0/00:24:d6:10:18:7e
Sending on Socket/fallback
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:24:d6:10:18:7e
Sending on LPF/eth0/00:24:d6:10:18:7e
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[ OK ]
ubuntu@ubuntu:~$

---

### Post by SpockVulcan on 2010-08-07
> I keyed in the necessary data, i.e. Ip, Subnet, Getaway, DNS 
In Network Tools 100% packets yet no www can be accessed thru FF :(
Why shouldn't you just click the network manager icon and join a network.

---

### Post by korbennn on 2010-08-07
I should and I can, that't the whole beauty of it! Yet no page loads in FF... a mystery remains

---

### Post by korbennn on 2010-08-09
I think it needs Marvell's driver

> install_v10.85.3.3.tar

how to install it?

---

### Post by Sef on 2010-08-09
> Listening on LPF/eth0/00:24:d6:10:18:7e
Sending on LPF/eth0/00:24:d6:10:18:7e
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

1) How are you connecting to the internet?

2) The problems lies with no DHCPOFFERS received.  The question is why?  Does the problem lie with your machine, the router, or other?  

3) Do you have another computer that can be hooked up to that net?  If it works, then the problem lies with your machine, and we can take it from there.

---

### Post by korbennn on 2010-08-15
I never thought I would do that...

downloaded, burned, ran Puppy 5.1 livecd, loaded sk98lin driver - wired **working**!

how come does it work on lil puppy but not in Ubu the giant?

any tips on how to make it work?

---

