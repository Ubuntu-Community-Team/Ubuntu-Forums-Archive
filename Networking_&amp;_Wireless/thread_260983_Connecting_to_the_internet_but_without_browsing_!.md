---
title: "Connecting to the internet but without browsing !"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by Mr. Me on 2006-09-19
Hi all, :) 
i have a probelem in my linux. 
i have a connection via sattlite. 

when i install ubuntu i was browsing the internet without any porolem. 
but now i can not ! 
i try to install linux again and still i have same problem i can not brousing the internet or update the system ! 

i never use proxy. 
also i try to use this command 
sudo ofsown eth0 
sudo ifup eth0 

there is no result ! 
and now i`m using windows Xp with same connection. its mean i dont have any problem eith the connection. 

check the attached image please !

---

### Post by madmetal on 2006-09-19
look for dns servers..

---

### Post by Mr. Me on 2006-09-19
Every thing ok ! 

Regards,

---

### Post by tbonius on 2006-09-19
Check /etc/network/interfaces file.  What entries are in here?

Check /etc/resolv.conf  What entries are in here?

Check /etc/hostname and /etc/hosts   What entries are in here?

ifdown eth0
ifup eth0

ifconfig -a

What is reurned for your IP configuration?

T

---

### Post by Mr. Me on 2006-09-19
Hi 
this is the result : 

Check /etc/network/interfaces file. What entries are in here?

[COLOR="Blue"]admin@localhost:~$ cat /etc/network/interfaces[/COLOR]
# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.

iface lo inet loopback

iface eth0 inet dhcp

auto eth0


[COLOR="blue"]Check /etc/resolv.conf What entries are in here?[/COLOR]

search odsplus.net
nameserver 82.167.0.131
nameserver 205.252.144.228

Check /etc/hostname and /etc/hosts What entries are in here?

[COLOR="blue"]admin@localhost:~$ cat /etc/hostname[/COLOR]
localhost
 -
[COLOR="blue"]admin@localhost:~$ cat /etc/hosts[/COLOR]
127.0.0.1 localhost


ifdown eth0

[COLOR="blue"]admin@localhost:~$ sudo ifdown eth0[/COLOR]
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:50:fc:75:1b:90
Sending on   LPF/eth0/00:50:fc:75:1b:90
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.192.4.20 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

ifup eth0

[COLOR="blue"]admin@localhost:~$ sudo ifup eth0[/COLOR]
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:50:fc:75:1b:90
Sending on   LPF/eth0/00:50:fc:75:1b:90
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 82.167.40.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 82.167.40.1
SIOCADDRT: Network is unreachable
bound to 82.167.40.24 -- renewal in 42482 seconds.


ifconfig -a
[COLOR="blue"]admin@localhost:~$ ifconfig -a[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:50:FC:75:1B:90
          inet addr:82.167.40.24  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::250:fcff:fe75:1b90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:433 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:47308 (46.1 KiB)  TX bytes:9023 (8.8 KiB)
          Interrupt:9 Base address:0xf00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:560 (560.0 b)  TX bytes:560 (560.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by tbonius on 2006-09-19
Network unreachable?  Are you being assigned a gateway?

netstat -rn

Ping your gateway.. any replies?  Ping a well know IP address like yahoo.com:

ping 209.131.36.158

any replies?

Also.. I assume you are directly connected to the DSL/Cable modem.. judging from the IP assigned.  Did you reboot the cable modem first?  Does your ISP do MAC address filtering?

T

---

### Post by Mr. Me on 2006-09-20
admin@localhost:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
82.167.40.0     0.0.0.0         255.255.252.0   U         0 0          0 eth0


admin@localhost:~$ ping 66.7.194.133
connect: Network is unreachable


admin@localhost:~$ ping [www.yahoo.com](www.yahoo.com)
ping: unknown host [www.yahoo.com](www.yahoo.com)


-- 
As i told you befor i`m using the internet via sattlite 
i reboot the modem severl times! 

Any suggestions ?

Regards,

---

### Post by Mr. Me on 2006-09-21
Any answer ?

---

