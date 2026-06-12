---
title: "dhclient"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by Fakircho on 2007-06-13
Can anyone tell me what dhclient does?
And why do i need to keep ruining this command in terminal for me to have internet access?

How can i get Ubuntu to this automatically every time ?

---

### Post by dbott67 on 2007-06-13
dhclient is the script that obtains the network settings for your NIC.  Under normal circumstances, it should be run automatically (so you shouldn't have to type it in a terminal).

First, can you post  the output of:
```
dbott@feisty:~$ [COLOR=Red]cat /etc/network/interfaces[/COLOR]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR=Red]auto[/COLOR] eth0
iface eth0 inet dhcp
```

The key part is 'auto eth0' (in my case).  It automatically enables eth0 on my system.  If your interfaces file is missing the 'auto' command in front of your primary interface, then this could be the trouble.

As an aside, you can force a command into the background (so that you can close the terminal, etc.) by adding an ampersand to the end:
```
sudo dhclient eth0 [COLOR=Red]&[/COLOR]
```

-Dave

---

### Post by Fakircho on 2007-06-13
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp

auto eth0

---

### Post by dbott67 on 2007-06-13
All looks good with your interfaces file.

Can you post the output of:
```
dbott@feisty:~$ **[COLOR=Red]ifconfig -a[/COLOR]**
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec0:a755/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3610415 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2798363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3358959840 (3.1 GiB)  TX bytes:1229939127 (1.1 GiB)
          Interrupt:17 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38033 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38033 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3189744 (3.0 MiB)  TX bytes:3189744 (3.0 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.177.1  Bcast:192.168.177.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.62.1  Bcast:172.16.62.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```and
```
dbott@feisty:~$ [COLOR=Red]**sudo  lshw -C network**[/COLOR]
Password:
  *-network
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c0:a7:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:17
```-Dave

---

### Post by Fakircho on 2007-06-13
eth0      Link encap:Ethernet  HWaddr 00:0D:61:53:A4:04  
          inet addr:172.16.29.231  Bcast:172.16.29.231  Mask:255.255.255.255
          inet6 addr: fe80::20d:61ff:fe53:a404/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:65093099 (62.0 MiB)  TX bytes:6841328 (6.5 MiB)
          Interrupt:18 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16224 (15.8 KiB)  TX bytes:16224 (15.8 KiB)

---

### Post by Fakircho on 2007-06-13
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@01:0b.0
       logical name: eth0
       version: 10
       serial: 00:0d:61:53:a4:04
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=172.16.29.231 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:d400-d4ff iomemory:ee000000-ee0000ff irq:18

---

### Post by Fakircho on 2007-06-13
Ok so i have posted the reults form 

ifconfig -a

sudo  lshw -C network

---

### Post by dbott67 on 2007-06-13
the ifconfig output looks good, as does your lshw output.  I don't know why the network interface does not start-up automatically.

1. Can you describe your network setup (ISP, cable/DSL, router, etc.)?

2. Have you installed any other network manager software?

-Dave

---

### Post by Fakircho on 2007-06-14
Hi dbott67

Thanks for helping me out. 

1 . I am not sure of the correct technical terms but i will try and describe my network setup. 
In the building where i stay there are network points in every flat and a company that provides internet through these. Tthey provide shared ADSL to the whole building. When you sign up they ask for the physical address of your network card which is smething like 00:0d:61:53:a4:04 and then they enter this into their system you pluch in your cable directly in the socket and everything works. Well it works automatically under Windows. Under Ubuntu (which i only installed on monday :) ) the internet worked the first time i booted into Ubuntu. Then i left my machine idel for a an few hours and when i came back the internet was not working. So i scratched around and found the dhclient thing which restores my internet connection but i have to enter in manually in theterminal everytime.

2. I have not installed any other network manager exept what Ubuntu installs by default.  

Does this information help ?

---

### Post by dbott67 on 2007-06-14
No problem.  A few things come to mind:

1. Check your log files (syslog & daemon.log) for any error messages related to dhclient:
```
dbott@feisty:~$ [COLOR=Red]**cat /var/log/syslog | grep dhclient**[/COLOR]
Jun 14 09:02:47 feisty dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 14 09:02:47 feisty dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 14 09:02:47 feisty dhclient: All rights reserved.
Jun 14 09:02:47 feisty dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jun 14 09:02:47 feisty dhclient: 
Jun 14 09:02:48 feisty dhclient: Listening on LPF/eth0/00:50:ba:c0:a7:55
Jun 14 09:02:48 feisty dhclient: Sending on   LPF/eth0/00:50:ba:c0:a7:55
Jun 14 09:02:48 feisty dhclient: Sending on   Socket/fallback
Jun 14 09:02:49 feisty dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jun 14 09:02:49 feisty dhclient: DHCPOFFER from 192.168.1.1
Jun 14 09:02:49 feisty dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 14 09:02:49 feisty dhclient: DHCPACK from 192.168.1.1
Jun 14 09:02:49 feisty dhclient: bound to 192.168.1.106 -- renewal in 230209 seconds.
```
```
dbott@feisty:~$ [COLOR=Red]**cat /var/log/daemon.log | grep dhclient**[/COLOR]
Jun 12 05:33:30 feisty dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Jun 12 05:33:30 feisty dhclient: DHCPACK from 192.168.1.1
Jun 12 05:33:31 feisty dhclient: bound to 192.168.1.106 -- renewal in 278945 seconds.
Jun 13 18:47:46 feisty dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 13 18:47:46 feisty dhclient: DHCPACK from 192.168.1.1
Jun 13 18:47:46 feisty dhclient: bound to 192.168.1.106 -- renewal in 265552 seconds.
Jun 14 09:02:47 feisty dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 14 09:02:47 feisty dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 14 09:02:47 feisty dhclient: All rights reserved.
Jun 14 09:02:47 feisty dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jun 14 09:02:47 feisty dhclient: 
Jun 14 09:02:48 feisty dhclient: Listening on LPF/eth0/00:50:ba:c0:a7:55
Jun 14 09:02:48 feisty dhclient: Sending on   LPF/eth0/00:50:ba:c0:a7:55
Jun 14 09:02:48 feisty dhclient: Sending on   Socket/fallback
Jun 14 09:02:49 feisty dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jun 14 09:02:49 feisty dhclient: DHCPOFFER from 192.168.1.1
Jun 14 09:02:49 feisty dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 14 09:02:49 feisty dhclient: DHCPACK from 192.168.1.1
Jun 14 09:02:49 feisty dhclient: bound to 192.168.1.106 -- renewal in 230209 seconds.
```

2. A number of weeks ago, another forum member was having similar problems and it turned out to be a setting he changed in his BIOS.  Resetting the BIOS to default values fixed the problem.

3. In a similar thread to yours, another member's network was also not starting during boot.  Basically, we crafted up a little script an had it run right after login.  This is the [thread]("http://ubuntuforums.org/showthread.php?t=408647") and the pertinent info is in post #16-#21.

Hope this helps.

---

### Post by Fakircho on 2007-06-14
Hi dbott67

I checked the logs and I am going to post the results of cat /var/log/daemon.log | grep dhclient
 This the is for the entire time i have had Ubuntu installed which is 4 days now :) its rather long 

cat /var/log/syslog | grep dhclient does not return anything ?

---

### Post by Fakircho on 2007-06-14
Jun 11 14:10:19 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5747
Jun 11 14:10:19 kiril dhclient: killed old client process, removed PID file
Jun 11 14:10:19 kiril dhclient: DHCPRELEASE on eth0 to 172.16.29.254 port 67
Jun 11 14:10:19 kiril dhclient: send_packet: Network is unreachable
Jun 11 14:10:19 kiril dhclient: send_packet: please consult README file regarding broadcast address.
Jun 11 14:11:18 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Jun 11 14:11:22 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jun 11 14:11:27 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jun 11 14:11:33 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jun 11 14:11:43 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jun 11 14:11:53 kiril dhclient: No DHCPOFFERS received.
Jun 11 16:24:50 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jun 11 16:24:53 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jun 11 16:25:00 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Jun 11 16:25:12 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Jun 11 16:25:21 kiril dhclient: No DHCPOFFERS received.
Jun 11 16:28:49 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 11 16:28:49 kiril dhclient: DHCPACK from 172.16.29.254
Jun 11 16:28:49 kiril dhclient: bound to 172.16.29.231 -- renewal in 21294 seconds.
Jun 11 17:02:12 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 4832
Jun 11 17:02:12 kiril dhclient: killed old client process, removed PID file
Jun 11 17:02:12 kiril dhclient: DHCPRELEASE on eth0 to 172.16.29.254 port 67
Jun 11 17:02:12 kiril dhclient: send_packet: Network is unreachable
Jun 11 17:02:12 kiril dhclient: send_packet: please consult README file regarding broadcast address.
Jun 11 17:02:23 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Jun 11 17:02:25 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jun 11 17:02:30 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Jun 11 17:02:41 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Jun 11 17:02:50 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jun 11 17:02:50 kiril dhclient: DHCPOFFER from 172.16.29.254
Jun 11 17:02:50 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 11 17:02:50 kiril dhclient: DHCPACK from 172.16.29.254
Jun 11 17:02:50 kiril dhclient: bound to 172.16.29.231 -- renewal in 16772 seconds.
Jun 11 17:38:10 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 11 17:38:10 kiril dhclient: DHCPACK from 172.16.29.254
Jun 11 17:38:10 kiril dhclient: bound to 172.16.29.231 -- renewal in 18812 seconds.
Jun 11 17:57:05 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 4809
Jun 11 17:57:05 kiril dhclient: killed old client process, removed PID file
Jun 11 17:57:05 kiril dhclient: DHCPRELEASE on eth0 to 172.16.29.254 port 67
Jun 11 17:57:05 kiril dhclient: send_packet: Network is unreachable
Jun 11 17:57:05 kiril dhclient: send_packet: please consult README file regarding broadcast address.
Jun 11 17:57:17 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Jun 11 17:57:19 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jun 11 17:57:25 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jun 11 17:57:38 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Jun 11 17:57:50 kiril dhclient: No DHCPOFFERS received.
Jun 11 17:59:54 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jun 11 17:59:54 kiril dhclient: DHCPOFFER from 172.16.29.254
Jun 11 17:59:54 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 11 17:59:54 kiril dhclient: DHCPACK from 172.16.29.254
Jun 11 17:59:54 kiril dhclient: bound to 172.16.29.231 -- renewal in 19639 seconds.
Jun 11 21:24:33 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 11 21:24:33 kiril dhclient: DHCPACK from 172.16.29.254
Jun 11 21:24:33 kiril dhclient: bound to 172.16.29.231 -- renewal in 20289 seconds.
Jun 11 21:26:01 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 4829
Jun 11 21:26:01 kiril dhclient: killed old client process, removed PID file
Jun 11 21:26:01 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 21:26:01 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 21:26:01 kiril dhclient: All rights reserved.
Jun 11 21:26:01 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 21:26:01 kiril dhclient: 
Jun 11 21:26:01 kiril dhclient: Listening on LPF/eth0/00:0d:61:53:a4:04
Jun 11 21:26:01 kiril dhclient: Sending on   LPF/eth0/00:0d:61:53:a4:04
Jun 11 21:26:01 kiril dhclient: Sending on   Socket/fallback
Jun 11 21:26:01 kiril dhclient: DHCPRELEASE on eth0 to 172.16.29.254 port 67
Jun 11 21:26:01 kiril dhclient: send_packet: Network is unreachable
Jun 11 21:26:01 kiril dhclient: send_packet: please consult README file regarding broadcast address.
Jun 11 21:26:15 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Jun 11 21:26:18 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jun 11 21:26:18 kiril dhclient: DHCPOFFER from 172.16.29.254
Jun 11 21:26:18 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 11 21:26:18 kiril dhclient: DHCPACK from 172.16.29.254
Jun 11 21:26:18 kiril dhclient: bound to 172.16.29.231 -- renewal in 20392 seconds.
Jun 11 21:35:16 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5558
Jun 11 21:35:16 kiril dhclient: killed old client process, removed PID file
Jun 11 21:35:16 kiril dhclient: DHCPRELEASE on eth0 to 172.16.29.254 port 67
Jun 11 21:35:16 kiril dhclient: send_packet: Network is unreachable
Jun 11 21:35:16 kiril dhclient: send_packet: please consult README file regarding broadcast address.
Jun 11 21:35:19 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Jun 11 21:35:23 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jun 11 21:35:23 kiril dhclient: DHCPOFFER from 172.16.29.254
Jun 11 21:35:23 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 11 21:35:23 kiril dhclient: DHCPACK from 172.16.29.254
Jun 11 21:35:23 kiril dhclient: bound to 172.16.29.231 -- renewal in 17274 seconds.
Jun 11 21:43:45 kiril dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Jun 11 21:43:45 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 21:43:45 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 21:43:45 kiril dhclient: All rights reserved.
Jun 11 21:43:45 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 21:43:45 kiril dhclient: 
Jun 11 21:43:47 kiril dhclient: Bind socket to interface: No such device
Jun 11 21:43:47 kiril dhclient: There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Jun 11 21:43:47 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 21:43:47 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 21:43:47 kiril dhclient: All rights reserved.
Jun 11 21:43:47 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 21:43:47 kiril dhclient: 
Jun 11 21:43:48 kiril dhclient: Bind socket to interface: No such device
Jun 11 21:43:48 kiril dhclient: There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Jun 11 21:43:48 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 21:43:48 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 21:43:48 kiril dhclient: All rights reserved.
Jun 11 21:43:48 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 21:43:48 kiril dhclient: 
Jun 11 21:43:49 kiril dhclient: Bind socket to interface: No such device
Jun 11 21:43:49 kiril dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Jun 11 21:43:49 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 21:43:49 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 21:43:49 kiril dhclient: All rights reserved.
Jun 11 21:43:49 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 21:43:49 kiril dhclient: 
Jun 11 21:43:51 kiril dhclient: Bind socket to interface: No such device
Jun 11 21:43:51 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6143
Jun 11 21:43:51 kiril dhclient: killed old client process, removed PID file
Jun 11 21:43:51 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 21:43:51 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 21:43:51 kiril dhclient: All rights reserved.
Jun 11 21:43:51 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 21:43:51 kiril dhclient: 
Jun 11 21:43:52 kiril dhclient: Listening on LPF/eth0/00:0d:61:53:a4:04
Jun 11 21:43:52 kiril dhclient: Sending on   LPF/eth0/00:0d:61:53:a4:04
Jun 11 21:43:52 kiril dhclient: Sending on   Socket/fallback
Jun 11 21:43:52 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 11 21:43:52 kiril dhclient: DHCPACK from 172.16.29.254
Jun 11 21:43:52 kiril dhclient: bound to 172.16.29.231 -- renewal in 18505 seconds.
Jun 11 23:03:54 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 11 23:03:54 kiril dhclient: DHCPACK from 172.16.29.254
Jun 11 23:03:54 kiril dhclient: bound to 172.16.29.231 -- renewal in 16843 seconds.
Jun 11 23:06:13 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 4837
Jun 11 23:06:13 kiril dhclient: killed old client process, removed PID file
Jun 11 23:06:13 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 23:06:13 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 23:06:13 kiril dhclient: All rights reserved.
Jun 11 23:06:13 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 23:06:13 kiril dhclient: 
Jun 11 23:06:14 kiril dhclient: Listening on LPF/eth0/00:0d:61:53:a4:04
Jun 11 23:06:14 kiril dhclient: Sending on   LPF/eth0/00:0d:61:53:a4:04
Jun 11 23:06:14 kiril dhclient: Sending on   Socket/fallback
Jun 11 23:06:14 kiril dhclient: DHCPRELEASE on eth0 to 172.16.29.254 port 67
Jun 11 23:06:14 kiril dhclient: send_packet: Network is unreachable
Jun 11 23:06:14 kiril dhclient: send_packet: please consult README file regarding broadcast address.
Jun 11 23:06:22 kiril dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Jun 11 23:06:22 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 23:06:22 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 23:06:22 kiril dhclient: All rights reserved.
Jun 11 23:06:22 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 23:06:22 kiril dhclient: 
Jun 11 23:06:24 kiril dhclient: Bind socket to interface: No such device
Jun 11 23:06:24 kiril dhclient: There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Jun 11 23:06:24 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 23:06:24 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 23:06:24 kiril dhclient: All rights reserved.
Jun 11 23:06:24 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 23:06:24 kiril dhclient: 
Jun 11 23:06:25 kiril dhclient: Bind socket to interface: No such device
Jun 11 23:06:25 kiril dhclient: There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Jun 11 23:06:25 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 23:06:25 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 23:06:25 kiril dhclient: All rights reserved.
Jun 11 23:06:25 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 23:06:25 kiril dhclient: 
Jun 11 23:06:26 kiril dhclient: Bind socket to interface: No such device
Jun 11 23:06:27 kiril dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Jun 11 23:06:27 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 23:06:27 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 23:06:27 kiril dhclient: All rights reserved.
Jun 11 23:06:27 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 23:06:27 kiril dhclient: 
Jun 11 23:06:28 kiril dhclient: Bind socket to interface: No such device
Jun 11 23:06:28 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Jun 11 23:06:28 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 23:06:28 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 23:06:28 kiril dhclient: All rights reserved.
Jun 11 23:06:28 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 23:06:28 kiril dhclient: 
Jun 11 23:06:29 kiril dhclient: Listening on LPF/eth0/00:0d:61:53:a4:04
Jun 11 23:06:29 kiril dhclient: Sending on   LPF/eth0/00:0d:61:53:a4:04
Jun 11 23:06:29 kiril dhclient: Sending on   Socket/fallback
Jun 11 23:06:30 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jun 11 23:06:30 kiril dhclient: DHCPOFFER from 172.16.29.254
Jun 11 23:06:30 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 11 23:06:30 kiril dhclient: DHCPACK from 172.16.29.254
Jun 11 23:06:30 kiril dhclient: bound to 172.16.29.231 -- renewal in 16326 seconds.
Jun 11 23:06:33 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 11 23:06:33 kiril dhclient: DHCPACK from 172.16.29.254
Jun 11 23:06:33 kiril dhclient: bound to 172.16.29.231 -- renewal in 16861 seconds.
Jun 11 23:07:57 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5869
Jun 11 23:07:57 kiril dhclient: killed old client process, removed PID file
Jun 11 23:07:57 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 23:07:57 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 23:07:57 kiril dhclient: All rights reserved.
Jun 11 23:07:57 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 23:07:57 kiril dhclient: 
Jun 11 23:07:57 kiril dhclient: Listening on LPF/eth0/00:0d:61:53:a4:04
Jun 11 23:07:57 kiril dhclient: Sending on   LPF/eth0/00:0d:61:53:a4:04
Jun 11 23:07:57 kiril dhclient: Sending on   Socket/fallback
Jun 11 23:07:57 kiril dhclient: DHCPRELEASE on eth0 to 172.16.29.254 port 67
Jun 11 23:07:57 kiril dhclient: send_packet: Network is unreachable
Jun 11 23:07:57 kiril dhclient: send_packet: please consult README file regarding broadcast address.
Jun 11 23:08:07 kiril dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Jun 11 23:08:07 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 23:08:07 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 23:08:07 kiril dhclient: All rights reserved.
Jun 11 23:08:07 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 23:08:07 kiril dhclient: 
Jun 11 23:08:08 kiril dhclient: Bind socket to interface: No such device
Jun 11 23:08:08 kiril dhclient: There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Jun 11 23:08:08 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 23:08:08 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 23:08:08 kiril dhclient: All rights reserved.
Jun 11 23:08:08 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 23:08:08 kiril dhclient: 
Jun 11 23:08:09 kiril dhclient: Bind socket to interface: No such device
Jun 11 23:08:09 kiril dhclient: There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Jun 11 23:08:09 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 23:08:09 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 23:08:09 kiril dhclient: All rights reserved.
Jun 11 23:08:09 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 23:08:09 kiril dhclient: 
Jun 11 23:08:10 kiril dhclient: Bind socket to interface: No such device
Jun 11 23:08:11 kiril dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Jun 11 23:08:11 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 23:08:11 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 23:08:11 kiril dhclient: All rights reserved.
Jun 11 23:08:11 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 23:08:11 kiril dhclient: 
Jun 11 23:08:12 kiril dhclient: Bind socket to interface: No such device
Jun 11 23:08:12 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Jun 11 23:08:12 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 23:08:12 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 23:08:12 kiril dhclient: All rights reserved.
Jun 11 23:08:12 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 23:08:12 kiril dhclient: 
Jun 11 23:08:13 kiril dhclient: Listening on LPF/eth0/00:0d:61:53:a4:04
Jun 11 23:08:13 kiril dhclient: Sending on   LPF/eth0/00:0d:61:53:a4:04
Jun 11 23:08:13 kiril dhclient: Sending on   Socket/fallback
Jun 11 23:08:14 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jun 11 23:08:14 kiril dhclient: DHCPOFFER from 172.16.29.254
Jun 11 23:08:14 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 11 23:08:14 kiril dhclient: DHCPACK from 172.16.29.254
Jun 11 23:08:14 kiril dhclient: bound to 172.16.29.231 -- renewal in 19617 seconds.
Jun 11 23:08:18 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 11 23:08:18 kiril dhclient: DHCPACK from 172.16.29.254
Jun 11 23:08:18 kiril dhclient: bound to 172.16.29.231 -- renewal in 17637 seconds.
Jun 11 23:08:51 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 11 23:08:51 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 11 23:08:51 kiril dhclient: All rights reserved.
Jun 11 23:08:51 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 11 23:08:51 kiril dhclient: 
Jun 11 23:08:52 kiril dhclient: Listening on LPF/eth0/00:0d:61:53:a4:04
Jun 11 23:08:52 kiril dhclient: Sending on   LPF/eth0/00:0d:61:53:a4:04
Jun 11 23:08:52 kiril dhclient: Sending on   Socket/fallback
Jun 11 23:08:53 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jun 11 23:08:53 kiril dhclient: DHCPOFFER from 172.16.29.254
Jun 11 23:08:53 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 11 23:08:53 kiril dhclient: DHCPACK from 172.16.29.254
Jun 11 23:08:53 kiril dhclient: bound to 172.16.29.231 -- renewal in 19799 seconds.
Jun 12 19:00:46 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 12 19:00:46 kiril dhclient: DHCPACK from 172.16.29.254
Jun 12 19:00:46 kiril dhclient: bound to 172.16.29.231 -- renewal in 18765 seconds.
Jun 12 19:02:00 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 4846
Jun 12 19:02:00 kiril dhclient: killed old client process, removed PID file
Jun 12 19:02:00 kiril dhclient: DHCPRELEASE on eth0 to 172.16.29.254 port 67
Jun 12 19:02:00 kiril dhclient: send_packet: Network is unreachable
Jun 12 19:02:00 kiril dhclient: send_packet: please consult README file regarding broadcast address.
Jun 12 19:02:11 kiril dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Jun 12 19:02:13 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jun 12 19:02:13 kiril dhclient: DHCPOFFER from 172.16.29.254
Jun 12 19:02:13 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 12 19:02:13 kiril dhclient: DHCPACK from 172.16.29.254
Jun 12 19:02:13 kiril dhclient: bound to 172.16.29.231 -- renewal in 19292 seconds.
Jun 12 19:03:27 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 12 19:03:27 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 12 19:03:27 kiril dhclient: All rights reserved.
Jun 12 19:03:27 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 12 19:03:27 kiril dhclient: 
Jun 12 19:03:28 kiril dhclient: Listening on LPF/eth0/00:0d:61:53:a4:04
Jun 12 19:03:28 kiril dhclient: Sending on   LPF/eth0/00:0d:61:53:a4:04
Jun 12 19:03:28 kiril dhclient: Sending on   Socket/fallback
Jun 12 19:03:30 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jun 12 19:03:30 kiril dhclient: DHCPOFFER from 172.16.29.254
Jun 12 19:03:30 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 12 19:03:30 kiril dhclient: DHCPACK from 172.16.29.254
Jun 12 19:03:30 kiril dhclient: bound to 172.16.29.231 -- renewal in 18421 seconds.
Jun 13 14:46:08 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 13 14:46:08 kiril dhclient: DHCPACK from 172.16.29.254
Jun 13 14:46:08 kiril dhclient: bound to 172.16.29.231 -- renewal in 18653 seconds.
Jun 13 14:47:27 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 13 14:47:27 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 13 14:47:27 kiril dhclient: All rights reserved.
Jun 13 14:47:27 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 13 14:47:27 kiril dhclient: 
Jun 13 14:47:28 kiril dhclient: Listening on LPF/eth0/00:0d:61:53:a4:04
Jun 13 14:47:28 kiril dhclient: Sending on   LPF/eth0/00:0d:61:53:a4:04
Jun 13 14:47:28 kiril dhclient: Sending on   Socket/fallback
Jun 13 14:47:29 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jun 13 14:47:29 kiril dhclient: DHCPOFFER from 172.16.29.254
Jun 13 14:47:29 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 13 14:47:29 kiril dhclient: DHCPACK from 172.16.29.254
Jun 13 14:47:29 kiril dhclient: bound to 172.16.29.231 -- renewal in 20400 seconds.
Jun 13 14:47:40 kiril dhclient: There is already a pid file /var/run/dhclient.pid with pid 5649
Jun 13 14:47:40 kiril dhclient: killed old client process, removed PID file
Jun 13 14:47:40 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 13 14:47:40 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 13 14:47:40 kiril dhclient: All rights reserved.
Jun 13 14:47:40 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 13 14:47:40 kiril dhclient: 
Jun 13 14:47:41 kiril dhclient: Listening on LPF/eth0/00:0d:61:53:a4:04
Jun 13 14:47:41 kiril dhclient: Sending on   LPF/eth0/00:0d:61:53:a4:04
Jun 13 14:47:41 kiril dhclient: Sending on   Socket/fallback
Jun 13 14:47:44 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 13 14:47:44 kiril dhclient: DHCPACK from 172.16.29.254
Jun 13 14:47:44 kiril dhclient: bound to 172.16.29.231 -- renewal in 20525 seconds.
Jun 13 18:50:23 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 13 18:50:23 kiril dhclient: DHCPACK from 172.16.29.254
Jun 13 18:50:23 kiril dhclient: bound to 172.16.29.231 -- renewal in 16924 seconds.
Jun 13 18:51:56 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 13 18:51:56 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 13 18:51:56 kiril dhclient: All rights reserved.
Jun 13 18:51:56 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 13 18:51:56 kiril dhclient: 
Jun 13 18:51:57 kiril dhclient: Listening on LPF/eth0/00:0d:61:53:a4:04
Jun 13 18:51:57 kiril dhclient: Sending on   LPF/eth0/00:0d:61:53:a4:04
Jun 13 18:51:57 kiril dhclient: Sending on   Socket/fallback
Jun 13 18:51:57 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 13 18:51:57 kiril dhclient: DHCPACK from 172.16.29.254
Jun 13 18:51:57 kiril dhclient: bound to 172.16.29.231 -- renewal in 17182 seconds.
Jun 13 23:32:27 kiril dhclient: DHCPREQUEST on eth0 to 172.16.29.254 port 67
Jun 13 23:32:27 kiril dhclient: DHCPACK from 172.16.29.254
Jun 13 23:32:27 kiril dhclient: bound to 172.16.29.231 -- renewal in 17526 seconds.
Jun 13 23:38:19 kiril dhclient: DHCPREQUEST on eth0 to 172.16.29.254 port 67
Jun 13 23:38:19 kiril dhclient: DHCPACK from 172.16.29.254
Jun 13 23:38:19 kiril dhclient: bound to 172.16.29.231 -- renewal in 18669 seconds.
Jun 14 18:20:02 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 14 18:20:02 kiril dhclient: DHCPACK from 172.16.29.254
Jun 14 18:20:02 kiril dhclient: bound to 172.16.29.231 -- renewal in 17603 seconds.
Jun 14 18:21:08 kiril dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun 14 18:21:08 kiril dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun 14 18:21:08 kiril dhclient: All rights reserved.
Jun 14 18:21:08 kiril dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 14 18:21:08 kiril dhclient: 
Jun 14 18:21:09 kiril dhclient: Listening on LPF/eth0/00:0d:61:53:a4:04
Jun 14 18:21:09 kiril dhclient: Sending on   LPF/eth0/00:0d:61:53:a4:04
Jun 14 18:21:09 kiril dhclient: Sending on   Socket/fallback
Jun 14 18:21:12 kiril dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jun 14 18:21:12 kiril dhclient: DHCPOFFER from 172.16.29.254
Jun 14 18:21:12 kiril dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 14 18:21:12 kiril dhclient: DHCPACK from 172.16.29.254
Jun 14 18:21:12 kiril dhclient: bound to 172.16.29.231 -- renewal in 17254 seconds.

---

### Post by Fakircho on 2007-06-15
I am going to try making the script  - wish me luck :)

---

