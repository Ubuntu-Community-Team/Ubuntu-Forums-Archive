---
title: "DNS Dynamic Update From DHCP"
date: 2015-09-09
forum: Networking &amp; Wireless
---

### Post by rnichols430 on 2015-09-09
I have everything working, but the reverse lookup.. I get this error:

Host XXX.X.X.xx.in-addr.arpa. not found: 3(NXDOMAIN)

Where would I look for this error? I have checked the zone files and they look like they should...

$ORIGIN .
$TTL 907200     ; 1 week 3 days 12 hours
X.X.xx.in-addr.arpa IN SOA      servername.here.lab. admin.here.lab. (
                                2014071402 ; serial
                                28800      ; refresh (8 hours)
                                604800     ; retry (1 week)
                                604800     ; expire (1 week)
                                86400      ; minimum (1 day)
                                )
                        NS      servername.here.lab.
$ORIGIN 0.0.10.in-addr.arpa.
1                       PTR     router.here.lab.
2                       PTR     servername.here.lab.
5                       PTR     nas.here.lab.
                        PTR     here.lab.

---

