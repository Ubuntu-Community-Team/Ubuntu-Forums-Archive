---
title: "SNMPTRAPD take time to execute an traphandle"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by olivier3 on 2013-09-05
Hi guy,

Ive beel configured a SnmpTrapd server with a handle and snmptrapd execute my script around 10s after received the traps.

My conf file is :
```
disableAuthorization yes
traphandle SNMPv2-SMI::enterprises.13732.99.1.* /home/a.out
```

i tried :

```
authCommunity log,execute public
traphandle SNMPv2-SMI::enterprises.13732.99.1.* /home/a.out
```

always around 10s after.
I would like that my script will be execute immedatly.

Someone know why this pb and how can i solve it?


Many thanks

---

