---
title: "network stops now and then"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by mvdberg112 on 2008-06-16
Gutsy.  2.6.22-14-generic   rtl8187
sometimes network stops working. dhclient might resolve, but mostly not. 
ifdown/ifup followed by dhclient often does work. 
I do not see a specefic error message, other then that the browser cannot reach the server anymore.

The problem happens both when setting Network Manager to roaming or not to roaming.
Using network manager, reselecting the location mostly works.
When set for some time to roaming, the nm-applet will usually pick up one of the wireless network, but this takes quite long. Even when set to 'roaming' it now and then stops working. When it stops working, reslecting the wireless network or another wireless network never helps (as it would normally). Doing ifdown/ifup when set to roaming does not work/help.
Reslecting the location in the network manager does help mostly, but not always.

When network works fine, dhclient gets renewal of IP address really quite (say within 5 seconds). When network is down, it takes about a minute. Does not seem the DHCP server, since Windows computer does not have this problem.

1. Who does have a suggestion for cause or solution?
2. If it would be conflict of software, which packages could I reinstall? 

Regards,
Michael

---

