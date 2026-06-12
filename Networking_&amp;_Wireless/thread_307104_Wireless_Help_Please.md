---
title: "Wireless Help Please"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by SirShaggy on 2006-11-26
Hello, I have a Belkin F5D7011 G+ card for my laptop. I found the driver here: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B) on line 1b 32. I downloaded the Dell driver and installed it. Here is what I have so far:

-----------------------------------------------------------------


shaggy@mundy-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0B:CD:A9:DC:A2
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fea9:dca2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:2600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1538369 (1.4 MiB)  TX bytes:363388 (354.8 KiB)
          Interrupt:10 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:11:50:F3:98:82
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:592 (592.0 b)  TX bytes:592 (592.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.191.1  Bcast:172.16.191.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.118.1  Bcast:172.16.118.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


--------------------------------------------------------------

shaggy@mundy-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid ShaggyAth0
wireless-key 4507ffeb0d8f7b4b65e8fcf6e0

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp





auto eth0

----------------------------------------------------------

shaggy@mundy-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

-------------------------------------------------------------

shaggy@mundy-laptop:~$ sudo lshw -C network
Password:
  *-network
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a9:dc:a2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=natsemi driverversion=1.07+LK1.0.17 duplex=full ip=192.168.2.3 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:2400-24ff iomemory:c0008000-c0008fff irq:10
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@02:00.0
       logical name: eth1
       version: 02
       serial: 00:11:50:f3:98:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-27-686 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:52000000-52001fff irq:11

---------------------------------------------------------------------

shaggy@mundy-laptop:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:11:50:f3:98:82
Sending on   LPF/eth1/00:11:50:f3:98:82
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
----------------------------------------------------------

shaggy@mundy-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:11:50:f3:98:82
Sending on   LPF/eth1/00:11:50:f3:98:82
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
shaggy@mundy-laptop:~$ 

Any ideas what I am doing wrong? I'd really like to make this work, I am just not sure at this point. I had a couple of other cards on other laptops, they worked great!?!? I really need some help here. As you can see, I have a key enabled, I'll change it when I get it working.
Thanks,
SirShaggy

PS - UPDATE I just did lspci-n and received:
shaggy@mundy-laptop:~$ lspci -n
0000:00:00.0 0600: 1002:cbb2 (rev 02)
0000:00:01.0 0604: 1002:7010
0000:00:06.0 0401: 10b9:5451 (rev 02)
0000:00:07.0 0601: 10b9:1533
0000:00:08.0 0703: 10b9:5457
0000:00:0a.0 0607: 1217:6972
0000:00:0b.0 0c03: 1106:3038 (rev 50)
0000:00:0b.1 0c03: 1106:3038 (rev 50)
0000:00:0b.2 0c03: 1106:3104 (rev 51)
0000:00:0c.0 0c00: 104c:8026
0000:00:10.0 0101: 10b9:5229 (rev c4)
0000:00:11.0 0680: 10b9:7101
0000:00:12.0 0200: 100b:0020
0000:01:05.0 0300: 1002:4337
0000:02:00.0 0280: 14e4:4318 (rev 02)  <-----This is my card

However, when you go to the link I gave in the first paragraph for ndiswrapper,
it says the pciid: 14e4:4320 which is under line 1b 32 and my output is for the 
Belkin F5D7010 card on line 1b 30?????? Is this my problem? Do I have a strange 
revision that uses a different chip and driver? My card states Rev 2 on it.

shaggy@mundy-laptop:~$ sudo ndiswrapper -l
Password:
Installed ndis drivers:
bcmwl5          driver present
bcmwl5a         driver present
your_driver     invalid driver!


Well, I guess I'll try to install a different driver tomorrow. I need to sleep.
Sorry for the huge post....

---

### Post by wieman01 on 2006-11-26
First of all, it appears you have installed the incorrect driver. Second, take a look at this:
> *-network DISABLED
It says that your wireless device is disabled. There could be a number of reasons:

1. Incorrect driver.
2. Ethernet cable plugged in while you're attempting to configure wireless.
3. You card has been switched off (search for a hardware switch).

---

### Post by SirShaggy on 2006-11-26
> **wieman01 said:**
> First of all, it appears you have installed the incorrect driver. Second, take a look at this:

It says that your wireless device is disabled. There could be a number of reasons:

1. Incorrect driver.
2. Ethernet cable plugged in while you're attempting to configure wireless.
3. You card has been switched off (search for a hardware switch).



I just looked for a switch, didn't see one. It is a PCMCIA card bus card. Second, I do believe after a few hours of searching that my driver is for
sure incorrect and I will try the correct one. I know where it is and how to install it. My first problem is, How do I uninstall the incorrect driver first?
I think my Ethernet cable was disconnected when I tried to enable wireless at first, right now I am using it though. I will disconnect it for sure when I get ready to try again.
SirShaggy

---

### Post by wieman01 on 2006-11-26
To uninstall the current driver, simply mark the package for "complete removal" using Synaptic. Then reinstall it. That's the safest way.

---

### Post by SirShaggy on 2006-11-26
> **wieman01 said:**
> To uninstall the current driver, simply mark the package for "complete removal" using Synaptic. Then reinstall it. That's the safest way.


Perfect. I will do that now. It will be about 3-5 hours before I post again. Have some things to do. Thanks so much for the help, it is very appreciated!
SirShaggy

---

### Post by shpook on 2006-11-26
As far as I know Belkin is open source friendly and there are GPLed drivers available for G cards.

I've had some experience with F5D7010 which uses rt2500 chipset and it worked out of the box with Ubuntu 6.06-6.10

Edit: Correction, F5D7011 seems to be using Broadcom chipset, so my experience won't be of much help :)

Your ndiswrapper -l output should say something along the lines of "driver installed, hardware present" if it is working correctly.

---

