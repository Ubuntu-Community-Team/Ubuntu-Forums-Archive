---
title: "Weird DNS issue."
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by jerquiaga on 2008-03-13
I've been playing with Ubuntu at my company, and am having a strange DNS issue. We have an odd windows domain name, which follows the convention: servername.company.local. If I ping a server from the Terminal, the name is successfully resolved. If I try and use any type of web browser or other application, the names don't get resolved. Anyone have any idea why that might be?

---

### Post by Eiríkr on 2008-03-13
The Avahi daemon (the Linux implementation of the zeroconf standard known on Mac OS as Bonjour) uses the _.local_ namespace by default.  Check if Avahi is running on your Ubuntu machine, and configure / disable / uninstall it as required to avoid this name collision issue.

---

