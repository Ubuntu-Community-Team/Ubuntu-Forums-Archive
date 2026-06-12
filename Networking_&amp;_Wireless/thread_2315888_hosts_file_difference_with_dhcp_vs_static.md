---
title: "hosts file difference with dhcp vs static"
date: 2016-03-03
forum: Networking &amp; Wireless
---

### Post by Paul Weaver on 2016-03-03
If you install with a DHCP address, your hostsfile is populated with your hostname pointing to 127.0.1.1

If you install with a static IP, your hostsfile is populated with your hostname pointing to that IP

I just wondered if there was a specific reason that either
1) dhclient doesn't update the hosts file?
2) static installation doesn't also use 127.0.1.1

---

