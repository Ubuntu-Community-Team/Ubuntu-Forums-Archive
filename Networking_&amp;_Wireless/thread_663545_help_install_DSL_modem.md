---
title: "help install DSL modem"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by baskerville on 2008-01-10
Problem: No internet connection.

Hardware: ThinkPad R40
OS: Ubuntu 6.10
DSL Modem: Siemens Speedstream 4200
Connection: Ethernet Cable
(connection works perfectly on Windows XP machine) 

_Procedure followed _(as suggested [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)) was:
1. Open Terminal
2. Enter:< sudo pppoeconf >

Output from ppoeconf:
*I found 1 ethernet device: eth0.Are all your ethernet interfaces listed above? (If No, mod conf will be started so you can load the card drivers manually).Or Press ESC to abort here.<Yes>  <No>*

3. Input to ppoeconf: <Yes>

Output from pppoeconf:

[I]Looking for PPPoE Access Concentrator on eth0 (multi-modem mode) ...
...
Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem.[/I]

-----

How do I interpret that last message from pppoeconf, and what do I do about it?

---

