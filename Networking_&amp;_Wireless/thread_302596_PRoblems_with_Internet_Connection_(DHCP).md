---
title: "PRoblems with Internet Connection (DHCP)"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by dtiziani on 2006-11-18
After a Reboot I couldn't get internet connection (via eth1) anymore! I don't know if it was about some update. :-? 

Here are some logs relevant.

If ANYONE can try to help me. I got a windows machine here just to fix it, but I need internet @ ubuntu/linux so I can continue my work.

```

dtiziani@corpse:/etc/network$ ping www.google.com
ping: unknown host www.google.com





dtiziani@corpse:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
172.16.44.0     *               255.255.255.0   U     0      0        0 vmnet1
192.168.251.0   *               255.255.255.0   U     0      0        0 vmnet8
201.82.16.0     *               255.255.240.0   U     0      0        0 eth1
169.254.0.0     *               255.255.0.0     U     0      0        0 eth2




dtiziani@corpse:~$ ping -c1 201.82.16.1
PING 201.82.16.1 (201.82.16.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

--- 201.82.16.1 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms



dtiziani@corpse:~$ cat /etc/resolv.conf 
search cps.virtua.com.br
nameserver 200.174.144.14
nameserver 200.174.144.15



eth0      Link encap:Ethernet  HWaddr 00:0E:A6:67:43:8F  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:0E:A6:59:59:B6  
          inet addr:201.82.20.90  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::20e:a6ff:fe59:59b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:366746 (358.1 KiB)  TX bytes:1184 (1.1 KiB)
          Interrupt:201 

eth2      Link encap:Ethernet  HWaddr 00:11:95:FE:A1:14  
          inet addr:169.254.250.211  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::211:95ff:fefe:a114/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:5166 (5.0 KiB)
          Interrupt:201 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.44.1  Bcast:172.16.44.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.251.1  Bcast:192.168.251.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)











dtiziani@corpse:~$ sudo /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 6395
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0e:a6:59:59:b6
Sending on   LPF/eth1/00:0e:a6:59:59:b6
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 200.174.144.15 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
                                                                         [ ok ]








dtiziani@corpse:~$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                                               There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0e:a6:59:59:b6
Sending on   LPF/eth1/00:0e:a6:59:59:b6
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 201.82.16.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 201.82.16.1
bound to 201.82.20.90 -- renewal in 2794 seconds.
                                                                                            [ ok ]




dtiziani@corpse:~$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                            There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0e:a6:59:59:b6
Sending on   LPF/eth1/00:0e:a6:59:59:b6
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 201.82.16.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 201.82.16.1
bound to 201.82.20.90 -- renewal in 4389 seconds.







dtiziani@corpse:~$ tail -f /var/log/messages
Nov 18 23:48:11 corpse kernel: [17179997.768000] skge eth1: disabling interface
Nov 18 23:48:59 corpse kernel: [17180045.368000] eth0: no link during initialization.
Nov 18 23:48:59 corpse kernel: [17180045.368000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 18 23:49:02 corpse kernel: [17180048.672000] skge eth1: enabling interface
Nov 18 23:49:04 corpse kernel: [17180050.364000] skge eth1: Link is up at 100 Mbps, full duplex, flow control tx and rx
Nov 18 23:52:39 corpse kernel: [17180265.528000] skge eth1: disabling interface
Nov 18 23:53:02 corpse kernel: [17180287.924000] eth0: no link during initialization.
Nov 18 23:53:02 corpse kernel: [17180287.924000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 18 23:53:04 corpse kernel: [17180289.824000] skge eth1: enabling interface
Nov 18 23:53:05 corpse kernel: [17180291.532000] skge eth1: Link is up at 100 Mbps, full duplex, flow control tx and rx


dtiziani@corpse:~$ tail -f /var/log/syslog
Nov 18 23:53:09 corpse avahi-daemon[4458]: Leaving mDNS multicast group on interface eth1.IPv4 with address 201.82.20.90.
Nov 18 23:53:09 corpse avahi-daemon[4458]: iface.c: interface_mdns_mcast_join() called but no local address available.
Nov 18 23:53:09 corpse avahi-daemon[4458]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov 18 23:53:09 corpse avahi-daemon[4458]: New relevant interface eth1.IPv4 for mDNS.
Nov 18 23:53:09 corpse avahi-daemon[4458]: Joining mDNS multicast group on interface eth1.IPv4 with address 201.82.20.90.
Nov 18 23:53:09 corpse avahi-daemon[4458]: Registering new address record for 201.82.20.90 on eth1.
Nov 18 23:53:09 corpse dhclient: bound to 201.82.20.90 -- renewal in 4389 seconds.
Nov 18 23:53:09 corpse ntpdate[6552]: can't find host ntp.ubuntu.com 
Nov 18 23:53:09 corpse ntpdate[6552]: no servers can be used, exiting
Nov 18 23:53:14 corpse kernel: [17180300.240000] eth1: no IPv6 routers present






tail -f /var/log/messages
Nov 18 23:26:22 corpse kernel: [17180319.824000] skge eth1: enabling interface
Nov 18 23:26:24 corpse kernel: [17180321.512000] skge eth1: Link is up at 100 Mbps, full duplex, flow control tx and rx
Nov 18 23:29:51 corpse kernel: [17180528.556000] skge eth1: disabling interface
Nov 18 23:29:58 corpse kernel: [17180535.416000] skge eth1: enabling interface
Nov 18 23:30:00 corpse kernel: [17180537.100000] skge eth1: Link is up at 100 Mbps, full duplex, flow control tx and rx
Nov 18 23:32:51 corpse kernel: [17180708.468000] skge eth1: disabling interface
Nov 18 23:33:14 corpse kernel: [17180731.548000] eth0: no link during initialization.
Nov 18 23:33:14 corpse kernel: [17180731.552000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 18 23:33:14 corpse kernel: [17180731.624000] skge eth1: enabling interface
Nov 18 23:33:16 corpse kernel: [17180733.312000] skge eth1: Link is up at 100 Mbps, full duplex, flow control tx and rx

```

---

### Post by spd106 on 2006-11-19
You don't seem to have a default route set. This should have been given out when you acquired and ip address through dhcp.

I can't tell you what address it should be since I don't know your network. Ask the admin or try capturing it from windows. Add it through **sudo ip route add default via ??? dev eth1**

---

### Post by dtiziani on 2006-11-19
I ended up by reinstalling ubuntu.

It was really weird that the DHCP was working just fine and because of something updated it broke my Internet configurations.

I just wanted to know WHERE to look to see what steps DHCP were taking and see what the problem was.

I tried syslog and messages but nothing useful came up. It was really weird to get "send_packet: Operation not permitted" and such.

Well, if someone can give me some hints I appreciate, but for now, the problem is "solved" (windows way -> reformat) ](*,)

---

### Post by stream303 on 2006-11-23
Ack!  too drastic. :)

Maybe the following might shed some light on possible dns issues and encourage you to try again....

[http://www.ubuntuforums.org/showthread.php?t=305275](http://www.ubuntuforums.org/showthread.php?t=305275)

---

