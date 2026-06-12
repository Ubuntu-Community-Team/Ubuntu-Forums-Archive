---
title: "Wireless Connection deauthenticating"
date: 2017-08-24
forum: Networking &amp; Wireless
---

### Post by mstruzek on 2017-08-24
I have a complicated issue with wireless connection.
Almost on every system boot my connection is not able to wire with AP.

I found some strange log statement in dmesg : 

wlp6s0: deauthenticating from <MAC 'TP-LINK_E791BD' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)

After restart of NetworkManager I have access to my AP, but is quite cumbersome to manually fire up NetworkManager on each system boot.
 
wilress-info dump : [https://pastebin.com/EzGeHjvv](https://pastebin.com/EzGeHjvv)

---

