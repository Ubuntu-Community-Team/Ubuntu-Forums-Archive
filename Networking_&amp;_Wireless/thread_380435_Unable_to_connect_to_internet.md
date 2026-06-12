---
title: "Unable to connect to internet"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by ld50 on 2007-03-09
I have recently installed Ubuntu and have been unable to access the internet.  I'm hoping someone here may have an idea as to what is going wrong. Here is some info... 

Distro: Ubuntu 6.10
Connection: Cable modem -> Linksys router -> Wired connection to computer

lspci
02:0c.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 10)

sudo ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:07:E9:C6:52:ED
inet addr:192.168.1.103 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::207:e9ff:fec6:52ed/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:9 errors:0 dropped:0 overruns:0 frame:0
TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2735 (2.6 KiB) TX bytes:12672 (12.3 KiB)

sudo dhclient eth1
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
listening on LPF/eth1/00:18:39:06:a6:d5
sending on LPF/eth1/00:18:39:06:a6:d5
sending on socket/fallback
recieve_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 255.255.255.255 port 67 interval 8
send_packet: Network is down
.
.
.
No DHCPOFFERS received.
No working leases in persistent database - sleeping

sudo dhclient eht0
Listening on LPF/eth0/00:07:e9:c6:52:ed
Sending on LPF/eth0/00:07:e9:c6:52:ed
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.103 -- renewal in 32464 seconds.

eth1 Link encap:Ethernet HWaddr 00:18:39:06:A65
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:11

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:80 errors:0 dropped:0 overruns:0 frame:0
TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:7813 (7.6 KiB) TX bytes:7813 (7.6 KiB)

sit0 Link encap:IPv6-in-IPv4
NOARP MTU:1480 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

I cannot access any webpages or even the router's address in firefox.  Does anyone have any ideas? thank you very much

---

### Post by Mr. C. on 2007-03-09
Your eth0 is the active NIC.  It has received its IP address via DHCP.

Please show output from a terminal window for the following commands:

```
ping 82.211.81.166
cat /etc/resolv.conf
```

MrC

---

### Post by ld50 on 2007-03-09
ping 82.211.81.166
connect: Network is unreachable

cat /etc/resolv.conf
search ma.dl.cox.net
nameserver 208.180.42.100
nameserver 208.180.42.68
nameserver 206.191.207.250

---

### Post by Mr. C. on 2007-03-09
Ok, good.  We now there is no connectivity beyond your router.  We know you have connectivity because you received a DHCP lease from the router.

Please show your routers/modems IP information (LAN IPs, WAN IPs, and all netmasks, gateways, etc.).

Let's see if there's a config issue there.

MrC

---

### Post by ld50 on 2007-03-09
local ip: 192.168.1.1
subnet mask:255.255.255.0
mac address:00:18:39:4D:8B:50
default gateway:74.192.36.1
dns1:208.180.42.100
dns2:208.180.42.68
MTU:1500

not sure if thats all you need as I know little about what any of that is

---

### Post by ld50 on 2007-03-09
ok, well i have no idea as to why or how but, my internet connection now works. as if by magic..... Thanks for the help though!

---

### Post by Mr. C. on 2007-03-10
It must just be your lucky day!

We won't know until problems occur again, but hopefully they won't.  I'm glad things are working for you now.

Cheers,
MrC

---

