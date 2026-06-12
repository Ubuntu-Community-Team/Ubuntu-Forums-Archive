---
title: "detect network ip address"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by sa125 on 2008-02-02
How can I detect my IP address on my wireless network? I'm trying to forward ports on my router to work with bittorrent, but I'm not sure what my machine's IP is. My router allots addresses in the form of 10.0.0.xxx, and I want to be able to set my system to be a specific address of that format. How can I do this on Gutsy?

---

### Post by hahahan on 2008-02-02
Sa125,

run "ifconfig" in a terminal, it will show you some line's like:

eth0      Link encap:Ethernet  HWaddr 00:12:79:C0:26:2C  
            inet addr:192.168.x.x  Bcast:192.168.x.255  Mask:255.255.255.0
            UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1

When you forward ports it might be better to configure you network static v.s. DCHP.
Menu>System>Administration>Network .....

regards,

---

