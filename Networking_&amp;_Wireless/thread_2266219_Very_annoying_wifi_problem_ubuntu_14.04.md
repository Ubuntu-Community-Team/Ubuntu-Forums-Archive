---
title: "Very annoying wifi problem ubuntu 14.04"
date: 2015-02-21
forum: Networking &amp; Wireless
---

### Post by jtapp92 on 2015-02-21
so ive been using my wifi all day with no problem, i went out to get a bite to eat and when i came back and woke up my computer the wifi started acting very weird. when i try to download something be it from software center or the inter net it loses connection and continuosly askes me for my password also if i try to watch a video it will do the same about every 30 seconds. the only way to get the connection back up is to diable/enable wifi. 

any thoughts as to what the problem could be would be appreciated.

---

### Post by tgalati4 on 2015-02-21
It could be interference.  How many networks do you see when you click on the WiFi icon?  Grab a smart phone and install WiFi Analyzer and walk around to see how many competing networks are in your location.  You might need to change your WiFi channel from "6" or "Auto" to something with less traffic.

It's also possible that your WiFi module needs to be reseated or that the antenna connection has worn out.  Since the wires run through the hinge, opening and closing the lid can cause the wires to break or short out.

Open a terminal and examine:

```
dmesg | tail -50
```

Look for wireless-related error messages.

---

