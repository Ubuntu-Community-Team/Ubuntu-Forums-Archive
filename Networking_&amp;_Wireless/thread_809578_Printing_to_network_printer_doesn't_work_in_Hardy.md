---
title: "Printing to network printer doesn't work in Hardy"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by peterdm on 2008-05-27
I'm trying to print to a network printer which is on a windows xp machine. The printer wizard says everything is okay, but when I try to print a test page the log /var/log/cups/error_log fills up with the following messages:

E [27/May/2008:20:19:03 +0200] [Job 24] No ticket cache found for userid=1000
E [27/May/2008:20:19:03 +0200] [Job 24] Can not get the ticket cache for peter
E [27/May/2008:20:19:06 +0200] cupsdAuthorize: Local authentication certificate not found!
E [27/May/2008:20:19:06 +0200] cupsdAuthorize: Local authentication certificate not found!
E [27/May/2008:20:19:06 +0200] cupsdAuthorize: Local authentication certificate not found!
E [27/May/2008:20:25:59 +0200] cupsdAuthorize: Local authentication certificate not found!
E [27/May/2008:20:25:59 +0200] cupsdAuthorize: Local authentication certificate not found!
E [27/May/2008:20:26:34 +0200] cupsdAuthorize: Local authentication certificate not found!
E [27/May/2008:20:26:34 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [27/May/2008:20:26:38 +0200] [Job 25] No ticket cache found for userid=0
E [27/May/2008:20:26:38 +0200] [Job 25] Can not get the ticket cache for root

Any suggestions how to fix this?

Thanks,

Peter

---

