---
title: "Libnss and Netgear N900 - maybe due to fix?"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by oceola2 on 2015-01-15
This is more curiosity than understanding and a fix.
Update of the following packages last week caused a break in the connection and loss of Internet access sending me to my wireless providers setup screen instead of to the bookmark or the several locations I tried to reach.
**History from Synaptic**
Commit Log for Thu Jan  8 08:49:55 2015
Upgraded the following packages:
bsd-mailx (8.1.2-0.20131005cvs-1) to 8.1.2-0.20131005cvs-1ubuntu0.14.04.1
libnss3 (2:3.17.1-0ubuntu0.14.04.1) to 2:3.17.1-0ubuntu0.14.04.2
libnss3-nssdb (2:3.17.1-0ubuntu0.14.04.1) to 2:3.17.1-0ubuntu0.14.04.2
mime-support (3.54ubuntu1) to 3.54ubuntu1.1

To fix this in both 14.04LTS  and 12.04.5LTS the following was done.
Turn on the ipv6 to automatic on the ipv6 tab in the wireless Network Connection panel.
Try your connection again.
If this doesn't work, disconnect  and disable WiFi in the Untiy drop down.
If using a mifi device turn it off, remove and re-insert the battery.
After doing this the connection seems to be solid again with ipv6 set to automatic or ignore, tried both.
I believe there may have been a fix in the  system which is affected by the libnss packages or they were the cause of the previous ipv6 issues causing logouts.

---

