---
title: "UPnP"
date: 2016-05-05
forum: Networking &amp; Wireless
---

### Post by Akarsh_Kharidehal on 2016-05-05
Hii all,
I want to know if we can monitor or check the bandwidth usage of my UPnP server being run on my router.I enabled UPnP feature on my router and UPnP server is working well,I now want to know if I can play with it like monitoring its bandwidth usage and things related to the bandwidth.Can anybody tell me how can I do it??
Regards
Akarsh

---

### Post by TheFu on 2016-05-06
It depends completely on the router to report use.  For example, pfsense has built-in bandwidth graphs [https://doc.pfsense.org/index.php/RRD_Graphs](https://doc.pfsense.org/index.php/RRD_Graphs) - most cheap, home, routers do not, but many do allow SNMP so data and logs can be sent to other machines for graphing.  If your router firmware supports that, then you can do it.

BTW, UPnP is bad for security.  Anytime a router configuration can be altered by a client, it is bad for security.

---

