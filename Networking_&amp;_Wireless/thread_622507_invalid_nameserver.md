---
title: "invalid nameserver"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by joacorapela on 2007-11-24
[SIZE="5"]Hello Forum,

I am unsuccessfully trying to connect to a wired network from my laptop in my office at school (running Ubuntu 7.04). The problem seems to be  that my laptop is getting an invalid IP address from an invalid nameserver. At school we use IP addresses of the form 128.125.*.* and the invalid dhcp server is assigning me the IP number 192.168.2.100 (which does not work).

The output from "networking restart" in my office follows:
[/SIZE]
 * Reconfiguring network interfaces...
 * There is already a pid file /var/run/dhclient.eth0.pid with pid 8633
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:eb:4c:21
Sending on   LPF/eth0/00:c0:9f:eb:4c:21
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPNAK from 128.125.20.31
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.100 -- renewal in 299566 seconds.

[SIZE="5"]However, when I move to another building, with the same laptop, I start talking to a good nameserver that assigns me IP addresses that work. 

The output of "networking restart" in this other building follows:
[/SIZE]
 * Reconfiguring network interfaces...
 * There is already a pid file /var/run/dhclient.eth0.pid with pid 5813
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:eb:4c:21
Sending on   LPF/eth0/00:c0:9f:eb:4c:21
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 128.125.253.245 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:eb:4c:21
Sending on   LPF/eth0/00:c0:9f:eb:4c:21
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 128.125.254.32
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 128.125.254.32
SIOCADDRT: File exists
bound to 128.125.153.11 -- renewal in 21502 seconds.
                                                                         [ OK]

[SIZE="5"]Can anybody tell me why could it be that in my office I am getting an invalid IP number?

I talked to the network administrator of the building where I have problems and he told me that the dhcp server is offering a valid IP address buy my computer seems not to be accepting the dhcp server offer and keeps on asking an invalid IP address.

My guess is that the dhcp server in my office is not well configured. But I certainly don't know enough to tell this to the network administrator. :)

I would greatly appreciate any help. Cordially, Joaquin[/SIZE]

[SIZE="5"]dhclient.conf
[/SIZE]
# Configuration file for /sbin/dhclient, which is included in Debian's
#   dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#   man page for more information about the syntax of this file
#   and a more comprehensive list of the parameters understood by
#   dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#   not leave anything out (like the domain name, for example), then
#   few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 128.125.253.183, 128.125.253.166, 128.125.253.136;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, host-name,
    netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
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

[SIZE="5"]my interfaces
[/SIZE]
auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth0

iface ath0 inet dhcp
wireless-essid sail

[SIZE="5"]the output of ifconfig:
[/SIZE]
ath0      Link encap:Ethernet  HWaddr 00:14:A4:3F:8C:B5
          inet6 addr: fe80::214:a4ff:fe3f:8cb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1264707 (1.2 MiB)  TX bytes:2004 (1.9 KiB)

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:EB:4C:21
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:feeb:4c21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:272493 (266.1 KiB)  TX bytes:1184 (1.1 KiB)
          Interrupt:20

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
         TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1651 (1.6 KiB)  TX bytes:1651 (1.6 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-A4-3F-8C-B5-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80310 errors:0 dropped:0 overruns:0 frame:156922
          TX packets:1113 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:6887278 (6.5 MiB)  TX bytes:53946 (52.6 KiB)
          Interrupt:23

[SIZE="5"]the output of route (at my office):
[/SIZE]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

[SIZE="5"]the output of route (at the other building):
[/SIZE]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     1000   0        0 eth0
128.125.0.0     *               255.255.0.0     U     0      0        0 eth0
default         rtr-gw-30.usc.e 0.0.0.0         UG    0      0        0 eth0

---

### Post by willca on 2007-11-24
Check out /etc/dhcp3/dhclient.conf

You can specify to reject an offer from a specific server.

Here is a snip example.

timeout 60;
retry 60;
reboot 10;
select-timeout 5;
initial-interval 2;
reject 192.33.137.209;  <---- this is where you specify to reject that source for that 192.168.x.x network.

[http://www.gsp.com/cgi-bin/man.cgi?section=5&topic=dhclient.conf#6](http://www.gsp.com/cgi-bin/man.cgi?section=5&topic=dhclient.conf#6)

---

### Post by BryceHarding on 2007-11-24
I'm a complete Linux newb but i have some experience troubleshooting wired/wireless networks.  I could be wrong but from what you are describing the issue may lie with the wired fact that you are connecting to wireless router that doesn't have access to the internet and that is preventing you from using a wired connection.

either the os or hardware seems to give priority to the wireless connections and when you attempt to connect to a wireless network your computer will try and use the gateway from the wireless connection ignoring the physical ethernet connection.

the ip address that the invalid dhcp server is giving you is in the range of ip addresses served up by a belkin wirelesss router.

if i am right you should be able to get arround this by turning off the wireless on the laptop. the os should then be able to use the wired connection to be used instead of the wireless one.

---

### Post by daengbo on 2007-11-25
What willca said will work, but for the network's sake, you need to find out who's running the DHCP server on 192.168.2.1. That service needs to be turned off or it will mess up other people trying to connect, as well. You're receiving the offer from the bad server before the correct offer comes.

Contact your network admin and tell him that you're gettting a DHCPOFFER from 192.168.2.1. That should start the ball rolling. 

There should be only one active DHCP server on any subnet, unless there is an extra for failover purposes.

---

### Post by joacorapela on 2007-11-25
Thanks guys. The solution of willca worked great! ;) And I will tell the network administrator about this bad nameserver.

Cordially, Joaquin

---

