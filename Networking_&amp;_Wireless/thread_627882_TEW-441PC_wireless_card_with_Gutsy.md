---
title: "TEW-441PC wireless card with Gutsy"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by chadjohnson on 2007-11-30
My wireless card, TEW-441PC only works half the time. When I boot, it never obtains an IP address (even when sitting next to my router) unless I run
```

ifdown ath0
ifup ath0

```
Even when I do that, half the time it still fails to get an IP address

```

DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I'm using WPA (v1 I believe). I do not have this trouble using WEP.

Any ideas?

---

### Post by chadjohnson on 2007-12-01
bump

---

