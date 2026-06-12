---
title: "dhclient not working anymore?"
date: 2005-05-16
forum: Networking &amp; Wireless
---

### Post by achilleos on 2005-05-16
Hi

when i installed hoary everything worked perfectly, but recently i changed my dvd-rom drive and now dhcp is not working anymore. This is obviously strange.

after the hardware upgrade i get the following message from dhclient:
```
root@brahma:/home/thomas # dhclient
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/eth0/00:20:ab:af:12:43
Sending on   LPF/eth0/00:20:ab:af:12:43
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

i am sure it is neither a hardware nor network problem, as things still work perfectly using other operating systems/live cds/etc.

i remember having this problem before the release of hoary. it suddenly appeared after an upgrade. unfortunatly i can't remember whether dhclient has been updated then.

searching through the forum i found that quite a lot of users have the same problem after upgrading or changing their hardware. maybe this isn't a dhclient problem after all.

does anybody know more about this?
friendly
achilleos

---

