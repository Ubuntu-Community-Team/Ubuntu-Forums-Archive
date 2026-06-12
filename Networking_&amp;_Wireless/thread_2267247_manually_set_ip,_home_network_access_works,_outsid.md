---
title: "manually set ip, home network access works, outside internet access doesn't"
date: 2015-02-28
forum: Networking &amp; Wireless
---

### Post by SXR on 2015-02-28
attached are screen shots that might help. I manually edited my IP so my server is always at the same location on my network for port forwarding reasons. Now my server cannot access the internet but its completely available on the network. any idea what I broke? 

[IMG]http://i.imgur.com/Q3r0kxi.png[/IMG]


[IMG]http://i.imgur.com/fe0b8J6.png[/IMG]


[IMG]http://i.imgur.com/jmkvSrZ.png[/IMG]

---

### Post by steeldriver on 2015-02-28
I'm not familiar with the webmin interface, but I don't see DNS server(s) defined anywhere? are you able to ping external hosts by IP address?

---

### Post by SXR on 2015-02-28
cortex@cortex:~$ ping google.com
ping: unknown host google.com
cortex@cortex:~$ ping 8.8.8.8
connect: Network is unreachable
cortex@cortex:~$

Theres this... if it helps. 

[IMG]http://i.imgur.com/U9yGXn1.png[/IMG]

---

### Post by steeldriver on 2015-02-28
Your broadcast looks wrong to me as well (should be .255 surely?) - why not select 'automatic'? the broadcast address may be inferred from the network and netmask

---

### Post by SXR on 2015-02-28
[http://i.imgur.com/m0qn9Vn.png](http://i.imgur.com/m0qn9Vn.png) this is after setting broadcast to automatic. nothing changes 


[IMG]http://i.imgur.com/m0qn9Vn.png[/IMG]

Found a simple workaround... I've always been better with hardware. Fixed 


[IMG]http://i.imgur.com/SsOVGZ1.png[/IMG]

---

