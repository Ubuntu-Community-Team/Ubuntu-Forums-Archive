---
title: "[SOLVED] dhclient error"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by xchecker on 2008-08-07
I am running Heron 8.04 with a Linksys WUSB54G wireless adapter.  The adapter worked OK initially using the rt2500usb driver installed, but after a day or two the connection started to fail intermittently and now hasn't been working at all for two days.

I get nowhere with Network Manager so I am trying one last time to manually configure the network as per
[http://ubuntuforums.org/show-thread.php?t=684495](http://ubuntuforums.org/show-thread.php?t=684495)

When I get to
sudo client -r wlan0

I get the following:
```
crichmond@brichmond-desktop:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:72:e9:26
Sending on   LPF/wlan0/00:12:17:72:e9:26
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
```

I consulted the README file at isc.org and added 255.255.255.255 as instructed but that didn't help.

Am I wasting my time trying this?  If I can't reconnect this way, then I will try moving the box downstairs so that I can get a wired connection and download ndiswrapper.  Do I need to just stop trying to restore the connection with the default rt2500usb driver and move on to ndiswrapper?

---

