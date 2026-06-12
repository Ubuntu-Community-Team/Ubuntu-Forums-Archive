---
title: "WLAN only works with essid-broadcast enabled network"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by irrlicht on 2006-10-29
I have a weird problem:

My wireless connection *only* works when I enable ESSID-broadcast of the router. If the essid is hidden, it won't connect. 
I'm running edgy on a laptop with ipw2100-card. Router is a Siemens Gigaset SE 515.
Can anyone help? I wouldn't want to broadcast the ESSID for security reasons.

**Edit:** I was able to resolve this by changing the router's config to use a ESSID that begins with a lowercase letter. The name is now entirely lowercase (first letter was uppercase before), and it works. 
The only explanation I can think of is that some component of the whole process keeps lowercasing the ESSID and the request is therefore rejected by the router. 
Can someone think of a way to find the culprit, I would like to file a bug report?!

Regards, Tim

---

