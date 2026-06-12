---
title: "Router breaks network"
date: 2005-08-14
forum: Networking &amp; Wireless
---

### Post by blauser on 2005-08-14
I've already looked through the forums and the wiki, but I couldn't find anything that matched my problem.  

Everything works fine when I've got my computer plugged directly into my cable modem.  I get my ip address and DNS server list through dchp.  When I get my Linksys WRT54g router (with the latest firmware from Linksys) and plug my NIC into that, during boot the configuring network devices set takes much longer and doesn't work.  I get to the desktop and have no connectivity.  

Here is the result of ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:A0:CC:E5:EE:7C
          inet6 addr: fe80::2a0:ccff:fee5:ee7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2772 (2.7 KiB)
          Interrupt:11 Base address:0xa400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12246 (11.9 KiB)  TX bytes:12246 (11.9 KiB)
```

And here is the result for route -n:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

I've found away to get myself up and running but it's pretty annoying.  I simply ifdown eth0, ifup eth0, ifdown eth0, ifup eth0, etc. until it works (usually the first or second ifup eth0).  After that I have no problems at all until I reboot.  Can anyone point me in the way of a fix for this?

Here's the output from a typical failed ifup eth0:

```
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:a0:cc:e5:ee:7c
Sending on   LPF/eth0/00:a0:cc:e5:ee:7c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Any help would be greatly appreciated.

Edit:

I figured it might to see what happens when the thing is actually working, so here's the successful ifup eth0:

```
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:a0:cc:e5:ee:7c
Sending on   LPF/eth0/00:a0:cc:e5:ee:7c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 37666 seconds.

```

the results of ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:A0:CC:E5:EE:7C
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:ccff:fee5:ee7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:421 errors:8 dropped:0 overruns:0 carrier:6
          collisions:99 txqueuelen:1000
          RX bytes:294879 (287.9 KiB)  TX bytes:71581 (69.9 KiB)
          Interrupt:11 Base address:0xa400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:417182 (407.4 KiB)  TX bytes:417182 (407.4 KiB)
```

and route -n:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by heimo on 2005-08-14
Try disabling ipv6. Edit /etc/modprobe.d/aliases, change line with 
 ```
alias net-pf-10 ipv6
to
alias net-pf-10 off # was ipv6

```

---

### Post by blauser on 2005-08-14
[QUOTE=heimo]Try disabling ipv6. [/QUOTE]

Sorry, heimo, I tried what you suggested, but no dice.  Same problem, same annoying solution.

---

### Post by cwaldbieser on 2005-08-14
Could it have something to do with the DHCP configuration on the router?

---

### Post by blauser on 2005-08-14
Well, everything works perfectly when I boot into my Windows 2000 Pro partition, and I do have the latest official firmware from Linksys.  I've looked at all the settings available in the router configuration, but nothing seems out of place.

---

### Post by cwaldbieser on 2005-08-14
[QUOTE=blauser]Well, everything works perfectly when I boot into my Windows 2000 Pro partition, and I do have the latest official firmware from Linksys.  I've looked at all the settings available in the router configuration, but nothing seems out of place.[/QUOTE]
Could it be a setting in your /etc/dhcp3/dhclient.conf?  I don't really know much about setting up DHCP besides the basic concepts, so maybe someone else can help you out there.  My config looks like:
```
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

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
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
``` 
Most everything appears to be commented out.  Some of the settings might be useful if you know what you are doing.  The man pages might be some help.

---

