---
title: "Trying to understand SNMP"
date: 2017-01-03
forum: Networking &amp; Wireless
---

### Post by cazz on 2017-01-03
Hi
I trying to see if I can monitor my trednet camera with Observium
When I add the ip to the camera it can read some of the information but not all.

Att first it say wrong manufacturer, that is ok but I get NULL on uptime.

so now I trying to see what SNMP info the trendnet camera give with snmpwalk

but I Think I have problem with the OID.

Not sure what I have to use to see what info the camera give.

I have try with 

```
snmpwalk -v 1 -c public IPADDRESS .1.3.6.1
```

but it does not say so much
It show alot of INTEGER and STRING but nothing I can understand is uptime.

---

### Post by The Cog on 2017-01-03
sysUpTime is 1.3.6.1.2.1.1.3.0

This lists some interesting OIDs: [http://www.alvestrand.no/objectid/1.3.6.1.2.1.1.html](http://www.alvestrand.no/objectid/1.3.6.1.2.1.1.html)

I think if you install package snmp-mibs-downloader then it will install a lot of common MIB files that describe many OIDs, and then your snmpwalk should be able to give you names rather than numbers for the OIDs.

---

### Post by cazz on 2017-01-03
ohh thanks for the replay

Yes when I did use the OID then it show the the update on some computers.
But not on the camera so maybe it does not have any support for uptime.

---

