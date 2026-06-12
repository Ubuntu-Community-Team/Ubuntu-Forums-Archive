---
title: "DHCP does not work with encryption"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by Ken Milburn on 2008-08-21
My first posting was "WPA Encryption not being accepted"
The problem appears to be DHCP related.

Following the Sticky posting "How To: Manual Network Configuration without the need for Network Manager" I discovered the following:
  1. My madwifi driver was not working  I got "Network:1 UNCLAIMED"
  2. My ndiswrapper with winxp driver does work.
  3. My logical name: wlan0
  4. Unencrypted Connection works.  I get the:
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.2.3 from 192.168.2.1
DHCPREQUEST of 192.168.2.3 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.3 from 192.168.2.1
bound to 192.168.2.3 -- renewal in 928144630 seconds.

However
   5. Attempts using encryption WEP or WPA1 or WPA2 do not work.
Using the command $ sudo dhclient -r wlan0

There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:58:9b:78:0f
Sending on   LPF/wlan0/00:1e:58:9b:78:0f
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

Using the command $ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:58:9b:78:0f
Sending on   LPF/wlan0/00:1e:58:9b:78:0f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

So, I take it that my DHCP doesn't want to talk to me if I use encryption.
The README at [www.isc.org/sw/dhcp/](www.isc.org/sw/dhcp/) had a couple of suggestions relating to sending all ones, which did not change the situation.

Can any one provide me direction?

---

### Post by tl3000 on 2008-08-21
> **Ken Milburn said:**
> My first posting was "WPA Encryption not being accepted"
The problem appears to be DHCP related.

Following the Sticky posting "How To: Manual Network Configuration without the need for Network Manager" I discovered the following:
  1. My madwifi driver was not working  I got "Network:1 UNCLAIMED"
  2. My ndiswrapper with winxp driver does work.
  3. My logical name: wlan0
  4. Unencrypted Connection works.  I get the:
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.2.3 from 192.168.2.1
DHCPREQUEST of 192.168.2.3 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.3 from 192.168.2.1
bound to 192.168.2.3 -- renewal in 928144630 seconds.

However
   5. Attempts using encryption WEP or WPA1 or WPA2 do not work.
Using the command $ sudo dhclient -r wlan0

There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:58:9b:78:0f
Sending on   LPF/wlan0/00:1e:58:9b:78:0f
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

Using the command $ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:58:9b:78:0f
Sending on   LPF/wlan0/00:1e:58:9b:78:0f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

So, I take it that my DHCP doesn't want to talk to me if I use encryption.
The README at [www.isc.org/sw/dhcp/](www.isc.org/sw/dhcp/) had a couple of suggestions relating to sending all ones, which did not change the situation.

Can any one provide me direction?

DHCP would not work until you're connected to your router.  With encryption enabled, the wireless connection is failing to associate with your network.  Thus, no DHCP.  See the following bug report and try the workaround posted near the end of the thread:

[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446)

Your description of the symptoms resembles this bug.  Try the two command line workaround posted by Chri at comment #46.

---

