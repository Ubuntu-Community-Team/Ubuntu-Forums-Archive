---
title: "&quot;unknown hardware address&quot;"
date: 2005-08-19
forum: Networking &amp; Wireless
---

### Post by Zaare on 2005-08-19
I'm trying to get my wireless connection running. I'm using D-Link DWL-G650+.
I used ndiswrapper to install the driver and everything worked fine.
When I run:
```
ndiswrapper -l
```
I get:
> Installed ndis drivers:
gplus   driver present, hardware present
And scanning finds the AP, so no problems there either.
But when I try:
```
sudo dhclient wlan0
```
I get:
> 
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0d:88:f0:54:31
Sending on   LPF/wlan0/00:0d:88:f0:54:31
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
...

Does anyone know what this means?

---

### Post by kirsche on 2005-08-20
got the same thing on my box.
check with iwconfig if you are connected to your access point

---

### Post by Zaare on 2005-08-21
I think I'm not, because *iwconfig* responds with *Access Point: 00:00:00:00:00:00*.

---

### Post by sir_badger on 2005-08-31
Did you get your connection to the AP working?
Everything works fine card + ndiswrapper, detecting the AP setting ESSID and Key but dhclient wlan0 says

.
.
.
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 
what can be wrong?

---

### Post by Zaare on 2005-08-31
Nope, haven't been able to connect to AP. I haven't found anything to try on that department.
And unfortunately, I don't know what the problem you're describing depends on.

---

