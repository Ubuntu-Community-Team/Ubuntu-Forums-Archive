---
title: "Repeatedly loose wireless"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by convert_mrta on 2008-09-10
Hello,

I repeatedly lose wireless connectivity several times a day.

Running Hardy on Acer 3680 laptop.  Have already learned that internal card does not work in Ubuntu so am using Hawking Tech PCMCIA card, and have been for over a month.  Problem is that without warning, I lose connection.  No predictable length of time before I lose connection.  I am using Wicd to try to keep connection or at least automatically reconnect, but it doesn't seem to help.  If I try to make Wicd manually connect, the progress bar sweeps, but IP address cannot be obtained.

My next step is to open terminal and execute 
sudo /etc/init.d/networking restart wlan1; sudo dhclient wlan1

Sometimes that reconnects me, sometimes not.

My last resort is to pull the PCMCIA card out, wait a couple of seconds, reinsert, and run sudo /etc/init.d/networking restart wlan1; sudo dhclient wlan1 again.  Usually I can get reconnected with this last resort.

I've read the WiFi FAQ and scoured the boards, but don't see a similar situation.

All of this restarting networking and resetting the PCMCIA card is getting old.  Can anyone suggest how I can find what's going on?  If you need to see a log, let me know.  Below is results of sudo /etc/init.d/networking restart wlan1; sudo dhclient wlan1 with both failure and success.

THANKS for all your help!

greg@laptop:~$  sudo dhclient wlan1
[sudo] password for greg: 
There is already a pid file /var/run/dhclient.pid with pid 16601
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan1/00:12:0e:0d:6f:19
Sending on   LPF/wlan1/00:12:0e:0d:6f:19
Sending on   Socket/fallback
DHCPREQUEST of 10.0.0.3 on wlan1 to 255.255.255.255 port 67
DHCPREQUEST of 10.0.0.3 on wlan1 to 255.255.255.255 port 67
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
Trying recorded lease 10.0.0.3
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.

--- 10.0.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
greg@laptop:~$ sudo /etc/init.d/networking restart wlan1; sudo dhclient wlan1
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan1.pid with pid 16461
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan1/00:12:0e:0d:6f:19
Sending on   LPF/wlan1/00:12:0e:0d:6f:19
Sending on   Socket/fallback
DHCPRELEASE on wlan1 to 10.0.0.1 port 67
There is already a pid file /var/run/dhclient.wlan1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan1/00:12:0e:0d:6f:19
Sending on   LPF/wlan1/00:12:0e:0d:6f:19
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
^[[A^[[                                                                  [ OK ]
There is already a pid file /var/run/dhclient.pid with pid 25877
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan1/00:12:0e:0d:6f:19
Sending on   LPF/wlan1/00:12:0e:0d:6f:19
Sending on   Socket/fallback
DHCPREQUEST of 10.0.0.3 on wlan1 to 255.255.255.255 port 67
DHCPREQUEST of 10.0.0.3 on wlan1 to 255.255.255.255 port 67
DHCPREQUEST of 10.0.0.3 on wlan1 to 255.255.255.255 port 67
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
Trying recorded lease 10.0.0.3
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.

--- 10.0.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.


~~~~At this point, no joy, so I pulled and reinserted the PCMCIA Card and reran network restart~~~

greg@laptop:~$ sudo /etc/init.d/networking restart wlan1; sudo dhclient wlan1
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan1.pid with pid 26179
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan1/00:12:0e:0d:6f:19
Sending on   LPF/wlan1/00:12:0e:0d:6f:19
Sending on   Socket/fallback
DHCPRELEASE on wlan1 to 10.0.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.wlan1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan1/00:12:0e:0d:6f:19
Sending on   LPF/wlan1/00:12:0e:0d:6f:19
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 10.0.0.3 from 10.0.0.1
DHCPREQUEST of 10.0.0.3 on wlan1 to 255.255.255.255 port 67
DHCPACK of 10.0.0.3 from 10.0.0.1
bound to 10.0.0.3 -- renewal in 32749 seconds.

---

### Post by dope540 on 2008-09-10
i know how you feel dude.

i got a compaq presario v3000 with a broadcom bcm4312 wireless card and after like 2-3 days, it kept getting disconnected. i know its not the router.

currently running opensuse 11 now.

would like to move back to ubuntu, until it can be fixed, im staying with suse.

---

