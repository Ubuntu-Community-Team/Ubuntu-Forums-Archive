---
title: "Edgy Kubuntu - wlassistant 'sees' but can't connect to access points"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by gmccreight on 2006-10-28
The wlassistant 'sees' but isn't able to connect to any access points.  It successfully completes the "/sbin/iwlist ath0 scan" command, which leads me to believe that the wireless card is supported (at least to an extent).  I ran "sudo wlassistant" from the terminal, and this is what its output was (while trying to connect to GoogleWiFi, which is unsecured):

Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

sit0      no wireless extensions.

Wireless interface(s): ath0
Permissions checked.
ifconfig_status: /sbin/ifconfig ath0
scan: /sbin/iwlist ath0 scan
Networks found: 20
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
Gateway address: 192.168.168.1
ACTION: CONNECT.
kill_dhcp: /sbin/dhclient -r ath0
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0e:9b:14:83:db
Sending on   LPF/ath0/00:0e:9b:14:83:db
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.168.1 port 67
ifup: /sbin/ifconfig ath0 up
iwconfig_set: /sbin/iwconfig ath0 mode managed channel 7 key off essid GoogleWiFi
iwconfig_ap: /sbin/iwconfig ath0 ap 00:0D:97:04:86:35
ifconfig_dhcp: /sbin/dhclient -q ath0
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134993416
kill_dhcp: /sbin/dhclient -r ath0
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0e:9b:14:83:db
Sending on   LPF/ath0/00:0e:9b:14:83:db
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.168.1 port 67
CONNECTION FAILED.
Application options saved.
Kernel socket closed.

---

### Post by gmccreight on 2006-10-29
Oddly, although it said the connection failed, it actually succeeded.  I accidentally pinged Yahoo, and realized that it is working.  I'll have to learn not to pay attention to "connection failed" messages.

---

### Post by askmeabouttruth on 2006-10-29
I have the same problem. It does not work. When I use wireless assistant, it says it cannot connect, then all of a sudden it seems like it is connected, but ssid did not change! So, if there are 2 networks available, wireless assistant will not switch between them.

Any ideas?

---

