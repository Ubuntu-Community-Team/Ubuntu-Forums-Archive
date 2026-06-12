---
title: "DNS server has no IPv6 access"
date: 2016-12-01
forum: Networking &amp; Wireless
---

### Post by Jim_Kajder on 2016-12-01
Running Ubuntu 16.04.1 LTS on Wired Ethernet connection.

[http://test-ipv6.com/](http://test-ipv6.com/) says score is 9/10, "Your DNS server (possibly run by your ISP) appears to have no access to the IPv6 Internet, or is not configured to use it"

ZyXEL PK5001Z (modem/router/wireless) is configured per the ISP instructions for IPv4 and IPv6, and says it has both IPv4 DNS (205.171.3.65, 205.171.2.65) and IPv6 DNS (2001:428::1, 2001:428::2)

Ubuntu Connection Information shows IPv4 Primary DNS as 192.168.0.1 and Secondary DNS as 205.171.2.65 (which makes sense, the Primary is the PK5001Z, and so I think Ubuntu is getting IPv4 DNS from the PK5001Z).

Is there a way I can get Ubuntu to use the IPv6 DNS that the PK5001Z is providing?

Jim

---

