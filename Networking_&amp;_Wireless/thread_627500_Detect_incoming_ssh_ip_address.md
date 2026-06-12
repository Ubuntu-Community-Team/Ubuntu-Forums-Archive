---
title: "Detect incoming ssh ip address"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by havencruise on 2007-11-30
Hi guys, 

Was wondering if there is a way(like a third party software,or a command) to detect any incoming SSH ip addresses to my system.

---

### Post by Fire_Chief on 2007-11-30
You can use netstat to see these connections. It will be default display all inbound and outbound connections to your system. The key field you are looking for is the foreign address. Open a terminal window and type```
netstat -an --inet
```Look for any foreign addresses listed with **:22** after it. This will tell you the source IPs connecting to you via SSH.

---

