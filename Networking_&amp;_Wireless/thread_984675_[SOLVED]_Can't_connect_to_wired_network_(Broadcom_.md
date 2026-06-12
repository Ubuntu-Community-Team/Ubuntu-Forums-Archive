---
title: "[SOLVED] Can't connect to wired network (Broadcom NetXtreme BCM5751)"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by frecon on 2008-11-16
When I try to connect to a wired network it just tries to connect but never succeeds.

Ubuntu 8.10
Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)


sudo dhclient eth0 
```

There is already a pid file /var/run/dhclient.pid with pid 6160 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

SIOCSIFADDR: No buffer space available 
Listening on LPF/eth0/00:11:43:05:e5:3f 
Sending on   LPF/eth0/00:11:43:05:e5:3f 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
send_packet: Message too long 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 
send_packet: Message too long 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 
send_packet: Message too long 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 
send_packet: Message too long 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 
send_packet: Message too long 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16 
send_packet: Message too long 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1 
send_packet: Message too long 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 

```

lspci
```

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04) 
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04) 
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04) 
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04) 
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) 
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) 
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) 
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03) 
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) 
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03) 
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01) 

```

---

### Post by pytheas22 on 2008-11-16
Try running these commands:

```
sudo sed 's/, interface-mtu//' /etc/dhcpd3/dhclient.conf
sudo ifconfig eth0 mtu 1500
sudo dhclient eth0
```

Does that get you connected?  [This thread]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/61989") suggests that it might solve the problem.

Also, do you have Windows on this machine?  And did this card ever work in Ubuntu?

---

### Post by frecon on 2008-11-17
> **pytheas22 said:**
> Try running these commands:

```
sudo sed 's/, interface-mtu//' /etc/dhcpd3/dhclient.conf
sudo ifconfig eth0 mtu 1500
sudo dhclient eth0
```

Does that get you connected?  [This thread]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/61989") suggests that it might solve the problem.

It didn't work. Seem to me that it didn't found the file dhclient.conf

```

ragnhild@ragnhild-desktop:~$ sudo sed 's/, interface-mtu//' /etc/dhcpd3/dhclient.conf 
[sudo] password for ragnhild: 
sed: kan inte läsa /etc/dhcpd3/dhclient.conf: Filen eller katalogen finns inte 
ragnhild@ragnhild-desktop:~$ sudo ifconfig eth0 mtu 1500 
ragnhild@ragnhild-desktop:~$ sudo dhclient eth0 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

Listening on LPF/eth0/00:11:43:05:e5:3f 
Sending on   LPF/eth0/00:11:43:05:e5:3f 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
ragnhild@ragnhild-desktop:~$ 

```

> **pytheas22 said:**
> Also, do you have Windows on this machine?  And did this card ever work in Ubuntu?
Windows was installed before and the network worked fine there. Now there's only Ubuntu installed. The network worked in Ubuntu 8.04 but then I did an automatic upgrade to 8.10 and it was then it stopped working. I double checked of course that there was no updates available before the upgrade.

I appreciate any help!

---

### Post by frecon on 2008-11-17
I did locate dhclient.conf and found it in /etc/dhcp3/dhclient.conf so I've changed the first command and got the following output. But it still doesn't work. :-(

```
ragnhild@ragnhild-desktop:~$ sudo sed 's/, interface-mtu//' /etc/dhcp3/dhclient.conf 
[sudo] password for ragnhild: 
# Configuration file for /sbin/dhclient, which is included in Debian's 
#	dhcp3-client package. 
# 
# This is a sample configuration file for dhclient. See dhclient.conf's 
#	man page for more information about the syntax of this file 
#	and a more comprehensive list of the parameters understood by 
#	dhclient. 
# 
# Normally, if the DHCP server provides reasonable information and does 
#	not leave anything out (like the domain name, for example), then 
#	few changes must be made to this file, if any. 
# 

send host-name "<hostname>"; 
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c; 
#send dhcp-lease-time 3600; 
#supersede domain-name "fugue.com home.vix.com"; 
#prepend domain-name-servers 127.0.0.1; 
request subnet-mask, broadcast-address, time-offset, routers, 
	domain-name, domain-name-servers, domain-search, host-name, 
	netbios-name-servers, netbios-scope; 
#require subnet-mask, domain-name-servers; 
#timeout 60; 
#retry 60; 
#reboot 10; 
#select-timeout 5; 
#initial-interval 2; 
#script "/etc/dhcp3/dhclient-script"; 
#media "-link0 -link1 -link2", "link0 link1"; 
#reject 192.33.137.209; 

#alias { 
#  interface "eth0"; 
#  fixed-address 192.5.5.213; 
#  option subnet-mask 255.255.255.255; 
#} 

#lease { 
#  interface "eth0"; 
#  fixed-address 192.33.137.200; 
#  medium "link0 link1"; 
#  option host-name "andare.swiftmedia.com"; 
#  option subnet-mask 255.255.255.0; 
#  option broadcast-address 192.33.137.255; 
#  option routers 192.33.137.250; 
#  option domain-name-servers 127.0.0.1; 
#  renew 2 2000/1/12 00:00:01; 
#  rebind 2 2000/1/12 00:00:01; 
#  expire 2 2000/1/12 00:00:01; 
#} 
ragnhild@ragnhild-desktop:~$ sudo ifconfig eth0 mtu 1500 
ragnhild@ragnhild-desktop:~$ sudo dhclient eth0 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

Listening on LPF/eth0/00:11:43:05:e5:3f 
Sending on   LPF/eth0/00:11:43:05:e5:3f 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
send_packet: Message too long 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
ragnhild@ragnhild-desktop:~$ 


```

---

### Post by pytheas22 on 2008-11-17
If you type:
```

sudo ifconfig eth0 mtu 1500
sudo dhclient eth0
```

does it work?  The ifconfig part is important.

It's also interesting that the output you're seeing while running dhclient is not consistent--in the first example, it spammed several times about 'message too long'; in the second example, it didn't mention this at all; in the third, the line only appears once.  I wonder if this might have more to do with your router than the Ubuntu client.  If possible (i.e. if this is a laptop), could you try connecting to a different wired network to see if you get the same results?

Also, have you tried using static IP?

---

### Post by frecon on 2008-11-18
I've tried to connect to a router first but then I tried directly to the modem and it worked. Here's the output:
```

ragnhild@ragnhild-desktop:~$ sudo ifconfig eth0 mtu 1500 
[sudo] password for ragnhild: 
ragnhild@ragnhild-desktop:~$ sudo dhclient eth0 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

Listening on LPF/eth0/00:11:43:05:e5:3f 
Sending on   LPF/eth0/00:11:43:05:e5:3f 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
DHCPOFFER of 192.168.0.34 from 192.168.0.1 
DHCPREQUEST of 192.168.0.34 on eth0 to 255.255.255.255 port 67 
DHCPACK of 192.168.0.34 from 192.168.0.1 
bound to 192.168.0.34 -- renewal in 6700 seconds. 
ragnhild@ragnhild-desktop:~$ 

```

But it still doesn't work to connect directly to the router. Any ideas to correct that?

---

### Post by pytheas22 on 2008-11-18
In the output you posted in your last post, you received an IP address, which is definitely a good sign (presumably the 'sudo ifconfig eth0 mtu 1500' command did the trick for that).  But you still couldn't load web pages thereafter?  Please post the output of these commands, in this order:
```

sudo killall NetworkManager
sudo ifconfig eth0 mtu 1500
sudo dhclient eth0
ifconfig eth0
host google.com
ping -c 5 google.com
ping -c 5 64.233.187.99
ping -c 5 192.168.0.1
```

---

### Post by frecon on 2008-11-19
Now it doesn't work to connect to the router OR the modem. :-( 

```
ragnhild@ragnhild-desktop:~$ sudo killall NetworkManager
[sudo] password for ragnhild:

ragnhild@ragnhild-desktop:~$ sudo ifconfig eth0 mtu 1500

ragnhild@ragnhild-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No buffer space available
Listening on LPF/eth0/00:11:43:05:e5:3f
Sending on LPF/eth0/00:11:43:05:e5:3f
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.0.32 from 192.168.0.1
DHCPREQUEST of 192.168.0.32 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.32 from 192.168.0.1
SIOCSIFADDR: No buffer space available
SIOCSIFADDR: No buffer space available
SIOCSIFNETMASK: Cannot assign requested address
SIOCSIFBRDADDR: Cannot assign requested address
SIOCADDRT: No such process
bound to 192.168.0.32 -- renewal in 6963 seconds.

ragnhild@ragnhild-desktop:~$ ifconfig eth0
eth0 Link encap:Ethernet HWaddr 00:11:43:05:e5:3f
inet6 addr: fe80::211:43ff:fe05:e53f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1188 (1.1 KB) TX bytes:1184 (1.1 KB)
Interrupt:16

ragnhild@ragnhild-desktop:~$ host google.com
;; connection timed out; no servers could be reached

ragnhild@ragnhild-desktop:~$ ping -c 5 google.com
ping: unknown host google.com

ragnhild@ragnhild-desktop:~$ ping -c 5 64.233.187.99
connect: Network is unreachable

ragnhild@ragnhild-desktop:~$ ping -c 5 192.168.0.1
connect: Network is unreachable

```

---

### Post by pytheas22 on 2008-11-19
Sorry it's still not working.  Very perplexing that it's getting an IP address but still can't seem to reach any network.

I did find this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284377") that looks possibly relevant.  It says that booting without Network Manager will resolve it (you have to get rid of NM completely; just killing it is not enough).  So I guess it's worth a try to uninstall NM:

```
sudo apt-get remove network-manager
```

Then reboot.  After rebooting, run:
```

sudo dhclient eth0
```

Does that get you an IP that you can actually use?

---

### Post by frecon on 2008-11-22
> **pytheas22 said:**
> sudo sed 's/, interface-mtu//' /etc/dhcpd3/dhclient.conf
sudo ifconfig eth0 mtu 1500
sudo dhclient eth0[/CODE]

This solved the problem. I have removed interface-mtu from dhclient.conf and changed the settings for the wired network to always use mtu 1500. :popcorn:

Thanks a lot!

---

