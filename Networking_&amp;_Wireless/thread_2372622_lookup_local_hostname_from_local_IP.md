---
title: "lookup local hostname from local IP"
date: 2017-09-27
forum: Networking &amp; Wireless
---

### Post by fuadk on 2017-09-27
Hi,
I am using Ubuntu as a bridge, and I need to lookup hostname from IP.
Ubuntu is connected to ISP router, and dhcp on router shows all names, and IP.
Ubuntu is configured to get IP from DHCP
I have one Ubuntu on VM, and able to resolve hostname from IP, another one on PC, was able to resolve before, and now it cant !!
I have reinstalled Ubuntu fresh today, installed inetutils, dnsutils, bind9.
[COLOR=#222222][FONT=arial]
I did not configure reverse DNS as this were working before without it.

What am I missing to get the lookup working?

Regards,
Fuad

[/FONT][/COLOR]

---

### Post by TheFu on 2017-09-27
DNS is how name resolution works on Linux.  For systems on your LAN, DNS is not automatic, it must be individually configured on a per IP basis.
As for external DNS resolution, it is most commonly provided by the router in a home environment, so just having the router's IP set as the DNS server should handle it.

BTW, The 4th statement is very confusing. I'm not 100% certain I understand it.

Or ... for LAN-to-LAN resolution, you can run avahi on all the systems.  Then the name resolution would be {hostname}.local.  Try that, since Avahi has been installed on most desktops automatically for years.

---

### Post by SeijiSensei on 2017-09-27
Are you pointing to the ISP's router when configuring DNS on your machine?

---

