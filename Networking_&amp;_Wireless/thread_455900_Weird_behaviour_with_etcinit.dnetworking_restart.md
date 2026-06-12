---
title: "Weird behaviour with /etc/init.d/networking restart"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by loreweaver on 2007-05-27
I have a problem with my wireless network (DHCP, Hidden SSID, WPA2, AES, ath0).
I actually got it working, but there's a weird behaviour I don't actually understand. Seems like everytime I want to get the wireless connection up, I need to invoke [FONT="System"]**sudo /etc/init.d/networking restart**[/FONT] twice:
> user1@xubuntubox:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.ath0.pid with pid 5055
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:b5:8b:fa:c3
Sending on   LPF/ath0/00:0f:b5:8b:fa:c3
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:b5:8b:fa:c3
Sending on   LPF/ath0/00:0f:b5:8b:fa:c3
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
user1@xubuntubox:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.ath0.pid with pid 5183
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:b5:8b:fa:c3
Sending on   LPF/ath0/00:0f:b5:8b:fa:c3
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:b5:8b:fa:c3
Sending on   LPF/ath0/00:0f:b5:8b:fa:c3
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.0.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.0.1
bound to 192.168.0.4 -- renewal in 37819 seconds.
                                                                         [ OK ]
user1@xubuntubox:~$ 
This problem can be replicated every time after restart. 
I have to put 2 lines of [FONT="System"]**sudo /etc/init.d/networking restart**[/FONT] in my [FONT="System"]**/etc/init.d/wireless-network.sh**[/FONT] to get my wireless running after boot.

Anyone knows what's going on here?
I'm happy to get wireless running, but I'm curious if there's a better way to get around this weird behaviour.

---

### Post by Fredizdman on 2008-05-05
I've been having exactly the same issue and I do know this is an old thread, its just a shame no one has found an answer in a year. Anyway, maybe I'll get lucky and someone will have an answer for me. All the details are basically the same. My card is also an atheros, which I'm guessing is why his connection was designated ath0 in the previous post.

The first /etc/init.d/networking restart fails after awhile claiming it received no DHCP offers.

The second /etc/init.d/networking restart is successful rather quickly (much faster than the previous) and I have no problems with my connection from then on.

---

