---
title: "Cannot connect to the Internet in Ubuntu"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by bhdenterprises on 2006-08-19
hello guys,

SOS pls... i was setting up a new ubuntu dapper in a computer with two
ethernet lan cards. got no problems during the installation. it even
said that the network was successfully configured. when i got to the
Ubuntu desktop, i found out that i have no internet conection. i
checked the networking tool in Ubuntu and it dispaled nameservers such
as merdiantelekoms.com and ip addresses. i have a new wireless DSL
thru Smart Bro that was installed the other day. my friend also has a
running Ubuntu with Smart Bro connection so I know it got to be a
hardware problem. my friend's NIC is realtek and mine are two Cnet PRO
200 PCI Fast  Ethernet Cards (as detected in Windows XP and as labeled
in the box). in ubuntu it is labeled Davicom Semiconductor Inc.
DEC-Tulip compatible 10/100 Ethernet (rev 40) when I run lspci.

tried to run dhclient and it said it got no DHCPOFFERS. checked
ifconfig what was registered was an IP6 address. i know it got to be
the cards cause my friend has no problems with realtek. now i have a
lame connection and instead of ubuntu alone in my box i was forced to
dual boot to WinXp for my internet purposes. i could not even download
ubuntu uodates and packages because i have no connection. please help
me guys..

command output:

harvey@webwires:/home/harvey# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:A1:A3:47:C3
         inet6 addr: fe80::208:a1ff:fea3:47c3/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:269 errors:0 dropped:0 overruns:0 frame:0
         TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:33679 (32.8 KiB)  TX bytes:15858 (15.4 KiB)
         Interrupt:5 Base address:0xe800

eth1      Link encap:Ethernet  HWaddr 00:08:A1:A3:3F:27
         inet6 addr: fe80::208:a1ff:fea3:3f27/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:5 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:28 dropped:0 overruns:0 carrier:28
         collisions:0 txqueuelen:1000
         RX bytes:1710 (1.6 KiB)  TX bytes:0 (0.0 b)
         Interrupt:5 Base address:0xe400

lo        Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:15 errors:0 dropped:0 overruns:0 frame:0
         TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:772 (772.0 b)  TX bytes:772 (772.0 b)

harvey@webwires:~$ sudo dhclient eth0
Password:
3Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:08:a1:a3:47:c3
Sending on   LPF/eth0/00:08:a1:a3:47:c3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

harvey@webwires:~$

thanks a lot...

---

### Post by anopheles on 2006-08-19
Perhaps your router does not have DHCP enabled, or you are not physically connected to it.

So: set up your NICs with static IP addresses, preferably in the range that your router's admin IP address lies in.

For example, the router might be at 192.168.0.1, so set up one of your NICs at 192.168.0.2.

You will need to find out your router admin address; set that as your default route.

Use the K/SystemSettings/Network tool to set up your NIC addresses and default route (that is for Kubuntu - use your ubuntu equivalent); 
or edit /etc/network/interfaces and then do 
$  /etc/init.d/networking restart

You should then be able to logon on to the router, maybe enable its DHCP server if that is what you really need.

---

### Post by bhdenterprises on 2006-08-19
anopheles,

thanks for your reply but i have already solve this problem five minutes after i posted it here. thanks a lot i am not the only one having problems with Cnet PRO 200. i found the answer here: [http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

i am now writing this reply inside ubuntu. this is the very reason why i love linux.. ubuntu in particular...

harvey

---

### Post by mikecar52 on 2006-08-19
turn off your ethernet card from system and see what happens

---

