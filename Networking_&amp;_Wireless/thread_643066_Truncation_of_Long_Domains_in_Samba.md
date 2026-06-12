---
title: "Truncation of Long Domains in Samba"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by r4e on 2007-12-17
In both Dolphin and Konqueror when connecting to Windows network shares with samba if the domain is really long it gets truncated from REALLYLONGDOMAIN\user to REA...AIN\user. Authentication subsequently fails resulting in the authentication box popping up again. If I retype in the full domain authentication succeeds, but on the next request if fails again and the authentication box pops up with the truncated domain. 

Both Dolphin and Konqueror switch the path to:

smb://REA...AIN\user@192.168.1.2/C$/

Is there a way to disable truncation of long domains?

Thanks in advance for your help!

r4e

---

