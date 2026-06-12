---
title: "wrt54g2 router and airave connection issues"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by cisopz on 2010-04-07
Jaunty 9.04 Linux, Motorola Surfboard SB5100 Cable Modem, Linksys WRT54G2 Wireless Router                   I can connect to the internet if I plug the modems ethernet cable directly into the computers ethernet port, but not if I have the modems ethernet cable connected to the Linksys WRT54G2 Router.          The airave is a Sprint independent tower to provide service to my cell phones, I have not even got to that step yet because I can't get the computer to access the internet though the router, anyways more on the airave later.

---

### Post by cisopz on 2010-04-07
james@ubuntu:~$ sudo dhclient
[sudo] password for james: 
There is already a pid file /var/run/dhclient.pid with pid 19825
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/02:b3:9e:dc:f8:fd
Sending on   LPF/pan0/02:b3:9e:dc:f8:fd
Listening on LPF/eth0/00:0c:76:94:94:3f
Sending on   LPF/eth0/00:0c:76:94:94:3f
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 3
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
james@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:94:94:3f  
          inet addr:63.145.249.164  Bcast:255.255.255.255  Mask:255.255.255.192
          inet6 addr: fe80::20c:76ff:fe94:943f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29435 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22991400 (22.9 MB)  TX bytes:4187663 (4.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:91910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4690627 (4.6 MB)  TX bytes:4690627 (4.6 MB)

pan0      Link encap:Ethernet  HWaddr 02:b3:9e:dc:f8:fd  
          inet6 addr: fe80::b3:9eff:fedc:f8fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:33325 (33.3 KB)

pan0:avahi Link encap:Ethernet  HWaddr 02:b3:9e:dc:f8:fd  
          inet addr:169.254.13.85  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

---

### Post by cisopz on 2010-04-07
james@ubuntu:~$ sudo dhclient
[sudo] password for james: 
There is already a pid file /var/run/dhclient.pid with pid 21025
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/02:b3:9e:dc:f8:fd
Sending on   LPF/pan0/02:b3:9e:dc:f8:fd
Listening on LPF/eth0/00:0c:76:94:94:3f
Sending on   LPF/eth0/00:0c:76:94:94:3f
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.1.2
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPOFFER of 192.168.1.100 from 192.168.1.2
DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.100 from 192.168.1.2
bound to 192.168.1.100 -- renewal in 40813 seconds.
james@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:94:94:3f  
          inet addr:192.168.1.100  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe94:943f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29499 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22994770 (22.9 MB)  TX bytes:4198868 (4.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92612 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92612 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4730567 (4.7 MB)  TX bytes:4730567 (4.7 MB)

pan0      Link encap:Ethernet  HWaddr 02:b3:9e:dc:f8:fd  
          inet6 addr: fe80::b3:9eff:fedc:f8fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:34747 (34.7 KB)

---

