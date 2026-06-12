---
title: "VPN and dns resolution"
date: 2005-07-10
forum: Networking &amp; Wireless
---

### Post by Confuse on 2005-07-10
I recently setup vpnc to connect to my school's vpn. All works and I can connect to the vpn but name resolution times out. I can ping ips, but I cannot resolve names. Bellow is my vpnc config (very simple). Any suggestions are highly appreciated. Thanks.

Damian

IPSec gateway IPADDRESS
IPSec ID IPSecUsers
IPSec secret PASSWORD
Xauth username MYUSERNAME
Xauth password MYPASSWORD

---

### Post by magoo on 2005-07-11
Try to check this:

have a look at the /etc/resolv.conf file, what IP do you see? If only the one of your ISP, then try to add manually the one of your school (see man page for the synthax)

does it help?

---

