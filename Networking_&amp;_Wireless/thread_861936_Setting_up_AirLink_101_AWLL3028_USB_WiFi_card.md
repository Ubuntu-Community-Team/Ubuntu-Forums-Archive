---
title: "Setting up AirLink 101 AWLL3028 USB WiFi card"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by pmulgaonkar on 2008-07-17
Hello folks.

I am using Hardy Heron 8.4.01

I have gone through the entire process of setting up the ndiswrapper for the drivers, etc. and am at the point where I am trying to connect to the AP. Everything works through the association with the AP, but it does not seem to get a DHCP address. 

The command before this: 
sudo iwconfig wlan0 essid <essid> key <hex key>
does not terminate with any errors.

However, the next step does not seem to result in a DHCP address assigned.

sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 7521
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:11:a3:05:44:63
Sending on   LPF/wlan0/00:11:a3:05:44:63
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Doing this through the gui results in a long time spent with the spinning blue arcs, but eventually returns to the prompt for the key.

Any ideas or help will be much appreciated.

--prasanna

---

