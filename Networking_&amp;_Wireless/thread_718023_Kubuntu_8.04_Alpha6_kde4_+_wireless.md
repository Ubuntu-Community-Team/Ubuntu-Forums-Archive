---
title: "Kubuntu 8.04 Alpha6 kde4 + wireless"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by RFPA on 2008-03-07
Hi everyone!

I'm having a little issue here with kde4. On my Kubuntu kde3.5.9 I have wireless working properly but in kde4.0.2 (Kubuntu alpha6 live cd) it doesn't connect to my wireless network. I've tried several times but doesn't seems to work.
The ESSID, encryption and passphrase are the same as in KDE3.5.9 but in Kde4 the knetworkmanager stops at 28% and no connection is obtained. Although, it recognizes my wireless network. 

Is this a bug or is something missing in my reasoning?

---

### Post by RFPA on 2008-03-09
Anyone? I've tried this how-to but nothing worked...

root@ricardo:~# ifconfig wlan0 down
root@ricardo:~# dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 11420
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:77:19:eb:71
Sending on   LPF/wlan0/00:1b:77:19:eb:71
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
root@ricardo:~# ifconfig wlan0 up
root@ricardo:~# iwconfig wlan0 essid "xpto"
root@ricardo:~# iwconfig wlan0 key 30fgg4b7di
root@ricardo:~# iwconfig wlan0 mode Managed
root@ricardo:~# dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:77:19:eb:71
Sending on   LPF/wlan0/00:1b:77:19:eb:71
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

This is what happens.

In kde 3.5.9 all worked well. 

Thanks

---

