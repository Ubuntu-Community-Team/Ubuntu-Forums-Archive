---
title: "Ubuntu Edgy Eft Wireless not working"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by redbaron1 on 2007-04-13
Hi,

I am a newbie to ubuntu, even though I have been using linux for a while. I had earlier successfully configured wireless  to work on my dell laptop(running ubuntu edgy eft). My wireless card  is broadcom and I had used firmware cutter. I use wlassistant to connect to my wireless network. My wireless network is not wep/wpa encrypted.
However since past 2 days I have not been able to connect to my wireless network.
I getting the following messages in the console. Can somebody please help me out?


john@madrid:~$ sudo wlassistant 
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Wireless interface(s): eth1
Permissions checked.
ifconfig_status: /sbin/ifconfig eth1
scan: /sbin/iwlist eth1 scan
Networks found: 15
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
Gateway address: 192.168.10.1
kill_dhcp: /sbin/dhclient -r eth1
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:18:f3:38:a3:73
Sending on   LPF/eth1/00:18:f3:38:a3:73
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.10.1 port 67
ifup: /sbin/ifconfig eth1 up
iwconfig_set: /sbin/iwconfig eth1 mode managed channel 6 key off essid default
iwconfig_ap: /sbin/iwconfig eth1 ap 00:13:46:C0:FC:04
ifconfig_manual: /sbin/ifconfig eth1 192.168.10.105 netmask 255.255.25.0 broadcast 192.168.10.255
==>stderr: SIOCSIFNETMASK: Invalid argument
resolv.conf: nameserver 192.168.10.1
route: /sbin/route add default gw 192.168.10.1
Checking for active connection.

---

