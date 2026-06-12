---
title: "Cant Ping Gateway and other PC"
date: 2005-10-09
forum: Networking &amp; Wireless
---

### Post by AntiMS on 2005-10-09
Hello, im new using Linux. I already download the file Linux Ubuntu 5.04.ISO and install in my pc using router. I just install Linux Ubuntu in 1 pc for test.

IP Adress = 192.168.1.10
Gateway = 192.168.1.1
DNS = 202.138.128.90, 202.138.28.128

what should i do, Static IP or DHCP i know about networking. Is there anyone here can tell STEP BY STEP configuration and what should be the best way and working. BTW im have 9 PC Winxp OS and 1 Linux Ubunte but Linux Ubunte cant connect to Internet and cant Ping other PC together with the Gateway (router).
The lan card detected and installed.

I already read and search some thread here but still cant connect. Waiting for reply...

---

### Post by costoa on 2005-10-09
Could you please post the output from 'ifconfig' and 'cat /etc/network/interfaces' ?

---

### Post by AntiMS on 2005-10-09
> ifconfig

eth0 
Link encap:Ethernet HWaddr 00:08:A1:7E: D0:04
inet addr:192.168.1.10 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80:208:alff:fe7e:d004/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:313 errors:0 dropped:0 overruns:0 frame:0
TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
callisions:0 txqueuel:1000
RX bytes 28819 (28.1 KiB) TX bytes:2772 (2.7 KiB)
Interrupt:11 Base address:0xd400

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP BROADCAST RUNNING MTU:16436 Metric:1
RX packets:902 errors:0 dropped:0 overruns:0 frame:0
TX packets:902 errors:0 dropped:0 overruns:0 carrier:0
callisions:0 txqueuel:0
RX bytes:80790 (78.8 KiB) TX bytes:80790 (78.8 KiB)


> cat /etc/network/interfaces
#The primary network interfaces

iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

I already set my LAN setting and is the settings. My Windows are doing fine for networking but my Ubunte Pc wasnt ping the Gateway (192.168.1.1) only my ubuntu can ping himself.

i try 

> sudo ifup eth0
ifup: interface eth0 already configured


What should be the next step after this. BTW thanks for the reply.

---

### Post by AntiMS on 2005-10-10
Hello, anybody....

---

### Post by costoa on 2005-10-10
ifconfig and interfaces look good. Assuming that you are using a combo router/switch (like a linksys or netgear) everything should work. Please post the output from: 'ping -c 3 127.0.0.1', 'ping -c 3 192.168.1.10' and 'ping -c 3 192.168.1.1'

BTW, while the forums here are good for researching and getting advice by their very nature there are delays. If you need a faster response you could try irc://irc.freenode.net/ubuntu .

---

### Post by SadaraX on 2005-10-10
I am having a similar problem. Actually, my ethernet connection was working fine until I decided I wanted to statically set the network IP.

I changed my /etc/network/interfaces to:

> 
auto eth0
iface eth0 inet static
  address 192.168.0.110
  netmask 255.255.255.0
  broadcast 192.168.0.255
  gateway 192.168.0.1


These were the settings I had for my previous linux install. I have used this configuration on 2 installations of Mepis Linux and 1 of Debian Woody. It has always worked just fine. 

After I made these changes from dhcp, and did 'ifdown eth0' and 'ifup eth0' as root, the system seemed alright. However, I could not get any connectivity. 

My browser does not work, neither my bittorrent. I cannot even ping the router. Actually, it looks like I cannot ping at all. I get the error message about problems with "sendmsg."

So, I reversed the settings back to what they had been:

> 
auto eth0
iface eth0 inet dhcp
  address 192.168.0.110
  netmask 255.255.255.0
  broadcast 192.168.0.255
  gateway 192.168.0.1


A quick ifdown/ifup and the system got an IP, however I still could not get connectivity. No ping and no working network. I have no idea how to fix this problem, because I have no idea what is wrong. I have even tried simply this in my /etc/network/interfaces:

> 
auto eth0
iface eth0 inet dhcp


But it does no good. What did I do to my network?

---

### Post by SadaraX on 2005-10-10
Sigh, never mind. I found out what my problem was and I feel rather foolish. I installed a firewall but did not configure it. :rolleyes:

---

### Post by AntiMS on 2005-10-10
Im using ZXDSL 831(router), sorry its my first time using Linux Ubuntu.

> ping -c 3 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes data.
64 bytes from 127.0.0.1 icmp_seq=1 ttl=64 time=0.088 ms
64 bytes from 127.0.0.1 icmp_seq=2 ttl=64 time=0.077 ms
64 bytes from 127.0.0.1 icmp_seq=3 ttl=64 time=0.075 ms

...127.0.0.1 ping statistics...
3 packets transmitted, 3 received , 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.075/0.080/0.088/0.005 ms


> ping -c 3 192.168.1.10
PING 192.168.1.10 (192.168.1.10) 56(84) bytes data.
64 bytes from 192.168.1.10 icmp_seq=1 ttl=64 time=0.079 ms
64 bytes from 192.168.1.10 icmp_seq=2 ttl=64 time=0.070 ms
64 bytes from 192.168.1.10 icmp_seq=3 ttl=64 time=0.075 ms

...192.168.1.10 ping statistics...
3 packets transmitted, 3 received , 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.070/0.074/0.079/0.010 ms


> ping -c 3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes data.
From 192.168.1.10 icp_seq=2 Destination Host Unreachable
From 192.168.1.10 icp_seq=3 Destination Host Unreachable

...192.168.1.1 ping statistics...
3 packets transmitted, 0 received , 100% packet loss, time 1999ms, pipe 2


i try to connect inm irc://irc.freenode.net/ubuntu but i am only one in that irc. 

its okay for me to wait just to fix my problem. Thanks anyway, waiting for your reply :D

---

