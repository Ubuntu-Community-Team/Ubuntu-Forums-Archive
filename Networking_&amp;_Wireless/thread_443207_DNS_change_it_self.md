---
title: "DNS: change it self"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by mzainal on 2007-05-14
Hi..
I already setup the dns. After 10min it change to 192.168.x.x my route ip. How to solve it?
[[IMG]http://img185.imageshack.us/img185/7392/dnsgb5.th.jpg[/IMG]](http://img185.imageshack.us/my.php?image=dnsgb5.jpg)

Thanks.

---

### Post by Austin_KW on 2007-05-14
Your dhcp is providing a dns server (your router) when it renews your IP address.

gksudo gedit /etc/dhcp3/dhclient.conf

Then either "prepend domain-name-servers yourDnsIpAddress"
or perhaps change the "request" so it does not ask for a dns server.

---

