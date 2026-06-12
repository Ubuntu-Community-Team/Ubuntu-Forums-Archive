---
title: "server IP address could not be found, 16.04"
date: 2018-04-23
forum: Networking &amp; Wireless
---

### Post by Coriander Redgoat on 2018-04-23
I'm running 16.04. I'm getting an error when I open most sites (not google or facebook) in Chrome (also firefox, but no problem on my other computer): (name of site)'s server IP address could not be found... ERR_NAME_NOT_RESOLVED.

I've tried 'clear host cache', but that didn't help.

Thanks!

---

### Post by TheFu on 2018-04-24
Seems like a DNS issue.  Which DNS are you using?  

Perhaps using a different DNS would help?  8.8.8.8 and 8.8.4.4 are google and believed to be safe & fast.  OpenDNS is another option, if you trust Cicso. Google will find it.  There are others and tools to find which DNS providers work the fastest for your network location.

All DNS has to be setup pointing at specific IP addresses.

---

### Post by Coriander Redgoat on 2018-04-24
It looks like I'm using 10.0.0.1. Adding 8.8.8.8 seems to have done it. Thanks!

---

### Post by TheFu on 2018-04-24
Please mark the thread as SOLVED using the thread tools near the top, if this is solved for you. It helps others in the community.

---

