---
title: "DHClient setting IP 0.0.0.0"
date: 2014-04-16
forum: Networking &amp; Wireless
---

### Post by michael140 on 2014-04-16
Hello
I have a possibly self inflicted issue with DHCP.
Recently I decided to set up a network bridge with eth0 to a dummy as a solution to another problem on a mythbuntu backend on another pc.I used a spare pc I had and made a back up of /etc/network/interface, installed bridge-utils  and enabled the dummy driver.I set the bridge to a fixed IP and disabled networkmanager .Prior to this dhcp has worked flawlessly for years .
Once I was satisfied with the results of my test I removed bridge-utils, disabled the dummy driver , replaced the changed interface from backup and re-enabled networkmanager.
Now I find that dhclient works fine when the lease has expired it will talk to the dhcp server on my ADSL modem and sets an appropiate IP.But if I restart the pc within the lease period Dhclient sets the IP to 0.0.0.0 as can be seen from the following syslog.

```
Apr  3 09:51:55 bachpvr-desktop dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Apr  3 09:51:55 bachpvr-desktop dhclient: Copyright 2004-2011 Internet Systems Consortium.
Apr  3 09:51:55 bachpvr-desktop dhclient: All rights reserved.
Apr  3 09:51:55 bachpvr-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr  3 09:51:55 bachpvr-desktop dhclient:
Apr  3 09:51:55 bachpvr-desktop dhclient: Listening on LPF/eth0/00:14:85:ce:cd:16
Apr  3 09:51:55 bachpvr-desktop dhclient: Sending on   LPF/eth0/00:14:85:ce:cd:16
Apr  3 09:51:55 bachpvr-desktop dhclient: Sending on   Socket/fallback
Apr  3 09:51:55 bachpvr-desktop dhclient: DHCPREQUEST of 192.168.1.4 on eth0 to 255.255.255.255 port 67
Apr  3 09:51:55 bachpvr-desktop dhclient: DHCPACK of 0.0.0.0 from 192.168.1.1
Apr  3 09:51:55 bachpvr-desktop dhclient: bound to 0.0.0.0 -- renewal in 41809 seconds.

```
I've checked with wireshark and the dhcp server never made that DHCPACK, so it seems that its possibly coming from a cache.
I have cleared the dhcp cache at /var/lib/dhcp/
I have reinstalled networkmanager
I have found that if I disable networkmanager and configure eth0 via the /etc/network/interface and enable dhcp there , dhcp works perfectly again.But as soon as network manager is re-enabled dhcp fails within the lease period.
The current /etc/network/interface document looks like this
```
auto lo
iface lo inet loopback
```

Ultimately I can just reinstall , but I am interested in trying to solve this and learn a bit more about linux.
If anyone can provide me with any guidance on how to diagnose this, I would much appreciate your help.

---

