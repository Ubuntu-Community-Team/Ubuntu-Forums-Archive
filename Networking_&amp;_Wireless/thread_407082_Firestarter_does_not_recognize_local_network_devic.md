---
title: "Firestarter does not recognize local network device (not ready)"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by stnever on 2007-04-11
Hello, I'm having trouble sharing my internet connection through Firestarter -- it complains that the device connected to my internal network is not ready.

uname -a:
Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

(i'm running directly from the Ubuntu 6.10 LiveCD).

This machine has three Ethernet ports:

eth0 - connected to a hub, through which 2 other machines connect to mine
eth1 - connected to my DSL modem
eth2 - VIA onboard, unplugged

First I ran pppoeconf, pretty straightforward (selected all "recommended" options, set username and password, and it worked).

Then I enabled the universe and multiverse repositories and did:

sudo apt-get install dchp

(Firestarter's user guide told me to do this to enable DHCP in my network. It installed, complained a bit at the end (but I don't have the exact messages, it was probably not yet configured)).

Then I installed firestarter through:

sudo apt-get install firestarter

Then I went into System > Administration > Firestarter and ran the wizard.

In the "internet connection" screen, I selected the "ppp0" connection. "Address is supplied by DHCP", "start firewall on dial-out" both checked.

In the "local network" connection I selected eth0, enabled connection sharing, and enabled DHCP.

When I started the firewall it complained:

Failed to start the firewall - the device eth0 is not ready. Check your network device and if your Internet connection is active.

I can browse the web normally (typing from the machine right now). If I change "eth0" to "eth1" it gives an unknown error (probably because eth1 is the DSL connection not the hub). "eth2" gives the same error as "eth0".

Any ideas? The same machine has a Windows installation that is correctly sharing the connection, so I doubt it's a broken cable or something. Is there any sort of log I can check to see the exact problem?

ifconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:E0:7D:D1:1D:81  
          inet6 addr: fe80::2e0:7dff:fed1:1d81/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37733 (36.8 KiB)  TX bytes:14328 (13.9 KiB)
          Interrupt:185 Base address:0x2c00 

eth1      Link encap:Ethernet  HWaddr 00:00:B4:C4:32:F9  
          inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::200:b4ff:fec4:32f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7093 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:15 txqueuelen:1000 
          RX bytes:9174884 (8.7 MiB)  TX bytes:577386 (563.8 KiB)
          Interrupt:193 Base address:0x4800 

eth2      Link encap:Ethernet  HWaddr 00:17:31:0D:D8:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:201.68.77.151  P-t-P:200.204.210.247  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:7000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:9014366 (8.5 MiB)  TX bytes:454818 (444.1 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


tail -f /var/log/syslog is not being too helpful...:

pr 11 19:30:08 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 11 19:30:13 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr 11 19:30:25 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Apr 11 19:30:44 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr 11 19:30:57 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr 11 19:31:09 ubuntu dhclient: No DHCPOFFERS received.
Apr 11 19:31:09 ubuntu dhclient: No working leases in persistent database - sleeping.
Apr 11 19:32:46 ubuntu kernel: [17181653.628000] Netfilter messages via NETLINK v0.30.
Apr 11 19:32:46 ubuntu kernel: [17181653.720000] ip_conntrack version 2.4 (4094 buckets, 32752 max) - 224 bytes per conntrack
Apr 11 19:32:48 ubuntu dhcpd: Internet Software Consortium DHCP Server 2.0pl5
Apr 11 19:32:48 ubuntu dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Apr 11 19:32:48 ubuntu dhcpd: All rights reserved.
Apr 11 19:32:48 ubuntu dhcpd: 
Apr 11 19:32:48 ubuntu dhcpd: Please contribute if you find this software useful.
Apr 11 19:32:48 ubuntu dhcpd: For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html)
Apr 11 19:32:48 ubuntu dhcpd: 
Apr 11 19:32:48 ubuntu dhcpd: No subnet declaration for eth1 (10.0.0.1).
Apr 11 19:32:48 ubuntu dhcpd: Please write a subnet declaration in your dhcpd.conf file for the
Apr 11 19:32:48 ubuntu dhcpd: network segment to which interface eth1 is attached.
Apr 11 19:32:48 ubuntu dhcpd: exiting.
Apr 11 19:32:54 ubuntu kernel: [17181661.420000] Inbound IN=ppp0 OUT= MAC= SRC=201.40.136.96 DST=201.68.77.151 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=64272 DF PROTO=TCP SPT=4448 DPT=1216 WINDOW=65535 RES=0x00 SYN URGP=0 
Apr 11 19:32:57 ubuntu kernel: [17181664.388000] Inbound IN=ppp0 OUT= MAC= SRC=201.40.136.96 DST=201.68.77.151 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=64371 DF PROTO=TCP SPT=4448 DPT=1216 WINDOW=65535 RES=0x00 SYN URGP=0 
Apr 11 19:33:03 ubuntu kernel: [17181670.440000] Inbound IN=ppp0 OUT= MAC= SRC=201.40.136.96 DST=201.68.77.151 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=9537 DF PROTO=TCP SPT=4448 DPT=1216 WINDOW=65535 RES=0x00 SYN URGP=0 
Apr 11 19:33:10 ubuntu dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
Apr 11 19:33:17 ubuntu dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
Apr 11 19:33:32 ubuntu dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
Apr 11 19:33:46 ubuntu dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 21
Apr 11 19:33:52 ubuntu dhcpd: Internet Software Consortium DHCP Server 2.0pl5
Apr 11 19:33:52 ubuntu dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Apr 11 19:33:52 ubuntu dhcpd: All rights reserved.
Apr 11 19:33:52 ubuntu dhcpd: 
Apr 11 19:33:52 ubuntu dhcpd: Please contribute if you find this software useful.
Apr 11 19:33:52 ubuntu dhcpd: For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html)
Apr 11 19:33:52 ubuntu dhcpd: 
Apr 11 19:33:52 ubuntu dhcpd: No subnet declaration for eth1 (10.0.0.1).
Apr 11 19:33:52 ubuntu dhcpd: Please write a subnet declaration in your dhcpd.conf file for the
Apr 11 19:33:52 ubuntu dhcpd: network segment to which interface eth1 is attached.
Apr 11 19:33:52 ubuntu dhcpd: exiting.
Apr 11 19:34:07 ubuntu dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 4
Apr 11 19:34:11 ubuntu dhclient: No DHCPOFFERS received.
Apr 11 19:34:11 ubuntu dhclient: No working leases in persistent database - sleeping.
Apr 11 19:34:36 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 11 19:34:41 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr 11 19:34:50 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 11 19:34:58 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr 11 19:35:08 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Apr 11 19:35:28 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr 11 19:35:37 ubuntu dhclient: No DHCPOFFERS received.
Apr 11 19:35:37 ubuntu dhclient: No working leases in persistent database - sleeping.

---

### Post by Bobrm2 on 2007-11-26
Not nearly as knowledgeable as you are but have the same problem, and with this error message:

Failed to start the firewall

The device ethois not ready.

Please check your network device settings and make sure your
internet connect is active.

Like you am connected via ath0, and on this machine from a WDA1310 ether net card to a WRB1320. Confused as to all wireless terms and their uses. 

Bob

---

### Post by Bobrm2 on 2007-11-26
should read connected from WDA1320 to a WBR1310.

---

### Post by andyanderso on 2008-04-14
I am also having this problem...I am connecting to the internet via a usb wireless modem through verizon...Then trying to share my internet connection through my wireless card.  Do I need to reconfigure my wireless card and if I do does that mean that I have to change the configuration every time I want to reconnect to the internet using my wireless?

This is as easy as clicking on internet sharing on my wife's mac...Is there an easy way to do this in Ubuntu?

andy

---

