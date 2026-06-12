---
title: "WPA2 not connecting."
date: 2009-05-01
forum: New to Ubuntu
---

### Post by rvgsd on 2009-05-01
Hi all, 
With my network manager, I am able to see all the wireless networks and also able to connect to the unsecured ones, but not to my WPA2 wireless with DHCP.
I followed instructions from this page:
[http://ubuntuforums.org/showthread.php?t=202834&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=202834&highlight=AR242x)

Still not successful and heres what happened:

My **'/etc/network/interfaces'** file looks like this:

```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid MYESSID
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk MY_HEX_KEY
```

so when I run **'sudo /etc/init.d/networking restart'**
here's what I get:

```

* Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 4764
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:2d:e7:e2
Sending on   LPF/wlan0/00:90:4b:2d:e7:e2
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:2d:e7:e2
Sending on   LPF/wlan0/00:90:4b:2d:e7:e2
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

(I also posted this message on the instructions thread, but no one seems to reply!)
What could be wrong? Any suggestions?
Thanks for helping out!

Regards,
RVGSD.

---

### Post by anewguy on 2009-05-01
Looks like it's not finding dhcp, which would indicate it either isn't reaching the router, or perhaps you need to specify the gateway address, dns server address, the network mask, etc. (as per the link - you can leave off the "address" line unless you want a static address).  Be sure to change the addresses to match your router.

Dave :)

---

