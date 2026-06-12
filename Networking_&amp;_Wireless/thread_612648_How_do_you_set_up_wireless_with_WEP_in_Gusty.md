---
title: "How do you set up wireless with WEP in Gusty"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by ianb72 on 2007-11-14
I am trying to set up a wireless setup for my dad in Gusty using a Linksys WUSB11v4 and ndiswrapper with the windoze drivers

It was working great under Feisty when we followed this post [http://ubuntuforums.org/showthread.php?t=422741]("http://ubuntuforums.org/showthread.php?t=422741")

We did how it said and uninstalled network-manager gnome and installed wifi radar.

We did a clean install of Gusty, and now in Gusty ndiswrapper is installed and so are the so are the windoze drivers, but do we follow the same route as we did in Feisty installing  wifi radar as we have found another post [http://ubuntuforums.org/showthread.php?t=602584]("http://ubuntuforums.org/showthread.php?t=602584")
Telling us to do it with the network manager, which we tried and all worked great till we got to adding the WEP key then we lost connection and could not get a IP address from the router.

When we run [HTML] sudo dhclient wlan0[/HTML]

We got this:
[HTML]mike@mike-desktop:~$ sudo dhclient wlan0
[sudo] password for mike:
There is already a pid file /var/run/dhclient.pid with pid 6741
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:12:17:97:84:bb
Sending on   LPF/wlan0/00:12:17:97:84:bb
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
mike@mike-desktop:~$ [/HTML]

Now as I said it all works great without the WEP key, so can anyone please help me/us out please??

Many thanks
Ian

---

