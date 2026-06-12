---
title: "Internet connection not detected"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by stoneage on 2008-07-19
I recently ran System => Administration => Hardware Testing, and found my system is not detecting my internet connection, which I found intriguing as I configured it manually after the auto set up failed to do it for me. I guess this may explain why 'ppp'
doesn't work either. It is set up as a 'Wired Connection'(dhcp), rather than pppoe. (I use 'ifup eth0' and 'ifdown eth0' instead)

I wondered if anyone knew what the problem might be. I have Virgin Media Broadband and have recently also been having trouble with my ISP e-mail accounts through Evolution. At first, of the two addresses I set up, the first ran fine and the second would only send but not receive mail, and now neither is working - I get no error or failure notices - mail simply fails to arrive, and when I click Send/Receive I get 'Could not connect to smpt.ntlworld.com: Connection refused'. Both Send and Receive addresses are whitelisted and stopping the Firewall doesn't resolve it - it just hangs. 

Could the two be related? I didn't contact my ISP yet - as far as I know they help only with Windows and Mac configuration questions and I would like to gather more information first.

I'm using 64 bit Hardy.
                                    
Any ideas?

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1a:4d:2e:22:2e  
          inet addr:82.11.48.208  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::21a:4dff:fe2e:222e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25905 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32927379 (31.4 MB)  TX bytes:2088249 (1.9 MB)
          Interrupt:21 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2709 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2709 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:122236 (119.3 KB)  TX bytes:122236 (119.3 KB)


dhclient

There is already a pid file /var/run/dhclient.pid with pid 1686
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:4d:2e:22:2e
Sending on   LPF/eth0/00:1a:4d:2e:22:2e
Sending on   Socket/fallback
DHCPREQUEST of 82.11.48.208 on eth0 to 255.255.255.255 port 67
DHCPACK of 82.11.48.208 from 10.191.124.1
bound to 82.11.48.208 -- renewal in 253513 seconds.

---

