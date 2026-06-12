---
title: "Network problems, sometimes"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by Piddell on 2008-07-06
Hi there, 
I've just upgraded to Heron and now have an intermittent internet connection.

3 times out of 4 I have to reboot both the PC and the Router to get the connection to work correctly.  Other PCs on the router work ok.

When not working I get this
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:55:3b:83:27  
          inet6 addr: fe80::202:55ff:fe3b:8327/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:322 (322.0 B)  TX bytes:810 (810.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

And if I try and connect to the router (let alone the internet) it fails to find it.

When the machine is working I get this output
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:55:3b:83:27  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:55ff:fe3b:8327/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:122822 (119.9 KB)  TX bytes:21825 (21.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Any thoughts?  Its a new feature which came with Heron ;-)

Thanks

Phill

---

### Post by Cjmovie on 2008-07-06
Hi,

Have you tried running ifdown / ifup on the link to see whether that fixes it? The output of when it's not working indicates that the link is OK, but it isn't configured, so you might try starting it back up again (which will reconfigure it for you by requesting an IP address from the router). Just run:

sudo ifdown eth0
sudo ifup eth0

You might also try the following:

sudo dhclient

Which will try and request configuration for the connection from your router. Also, if you run the second command (dhclient), what is the output?

---

### Post by Piddell on 2008-07-10
Thanks Cj
the ifdown and ifup did the trick:

sudo ifdown eth0
sudo: unable to resolve host phill-desktop
[sudo] password for phill: 
There is already a pid file /var/run/dhclient.eth0.pid with pid 4099
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:55:3b:83:27
Sending on   LPF/eth0/00:02:55:3b:83:27
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
phill@phill-desktop:~$ sudo ifup eth0
sudo: unable to resolve host phill-desktop
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:55:3b:83:27
Sending on   LPF/eth0/00:02:55:3b:83:27
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.1.3 from 192.168.1.1
DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.3 from 192.168.1.1
bound to 192.168.1.3 -- renewal in 40553 seconds.
phill@phill-desktop:~$ 


I'll see how it goes and if it still plays up I'll give it the old dhclient command.

Thanks

Phill

---

### Post by Piddell on 2008-07-11
Mmm same problem again today, so I ran

sudo dhclient
sudo: unable to resolve host phill-desktop
[sudo] password for phill: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:55:3b:83:27
Sending on   LPF/eth0/00:02:55:3b:83:27
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.3 from 192.168.1.1
DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.3 from 192.168.1.1
bound to 192.168.1.3 -- renewal in 37946 seconds.
phill@phill-desktop:~$ 

again we are back on-line, will this be a permanent fix?

---

