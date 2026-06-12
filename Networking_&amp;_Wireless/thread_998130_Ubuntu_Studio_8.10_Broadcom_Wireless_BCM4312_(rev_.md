---
title: "Ubuntu Studio 8.10 Broadcom Wireless BCM4312 (rev 1) not working."
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by pococinco on 2008-11-30
Using Ubuntu Studio 8.10 - The proprietary Broadcom Wireless driver is enabled. I can't find the place to input my Wireless SSID. Here is my info:

1) Machine Brand and Model (PC/Laptop): S10 Lenovo Ideapad Model 4231
2) Wireless Brand, Model and Wireless Chipset:
$ lspci -nn | grep 'Broadcom'
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
3) check interface:
$ iwconfig
eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated
4) Check for modules:
$ lsmod | grep "wl"
wl                   1076372  0 
5) Kernel boot messages:
$ dmesg | grep 'eth1'
[   17.950281] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.6
[   47.000071] eth1: no IPv6 routers present
[ 1978.828469] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.6
[ 1989.392089] eth1: no IPv6 routers present
6) Network Configuration:
sudo lshw -C network
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:50:72:97
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
7) Scan for networks:
$ iwlist scan | grep 'eth1'
eth1      Interface doesn't support scanning.
8) Ubuntu Version:
$ lsb_release -d
Description:	Ubuntu 8.10
9) Kernel/architecture (including 32 vs. 64 bit): 
$ uname -mr
2.6.27-9-generic i686
10) Restarting the network:
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          

There is already a pid file /var/run/dhclient.eth0.pid with pid 13825
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1e:68:ac:ee:0f
Sending on   LPF/eth0/00:1e:68:ac:ee:0f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1e:68:ac:ee:0f
Sending on   LPF/eth0/00:1e:68:ac:ee:0f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.105 from 192.168.1.1
DHCPREQUEST of 192.168.1.105 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.105 from 192.168.1.1
bound to 192.168.1.105 -- renewal in 33570 seconds.

---

### Post by Ayuthia on 2008-11-30
You might try the following from the Terminal:
```
sudo dhclient -r 
sudo iwconfig eth1 essid name-of-router
sudo dhclient eth1

```and see if that works.  If so, then it looks like the driver might not have scanning capabilities with your card.

---

### Post by pococinco on 2008-11-30
Here is the output of the terminal:

$ sudo dhclient -r
 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:21:00:50:72:97
Sending on   LPF/eth1/00:21:00:50:72:97

$ sudo iwconfig eth1 essid WRT54G
$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 16447
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:21:00:50:72:97
Sending on   LPF/eth1/00:21:00:50:72:97
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

To your question on scanning capabilities: I first installed Ubuntu 8.10 and was the wireless worked well both out of the box as with the proprietary driver from Broadcom. Now, after a complete wipe & install of Ubuntu Studio 8.10, I can't seem to get wireless going.

Another point of interest may be from the Network Connections screen:

Please contact your system administrator to resolve the following problem:

Could not find information on interface 'eth1:avahi' in /proc/net/dev

thanks!
Michel.

---

### Post by pococinco on 2008-11-30
I fixed it. Ubuntu Studio did not have Network Manager installed.

$ sudo apt-get install network-manager-gnome

Reboot
Use "Network Configuration" and add a Wireless network with SSID

$ sudo /etc/init.d/networking restart

And it worked...:)

---

