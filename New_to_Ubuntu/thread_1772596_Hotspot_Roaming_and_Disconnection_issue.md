---
title: "Hotspot Roaming and Disconnection issue"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by redmorning on 2011-05-31
Hi folks,

OS: Ubuntu 10.04

I'm connecting to a hotspot modem. When i watch my syslog (var tail -f /var/log/syslog) i see:
```
Jun  1 01:16:34 ganj NetworkManager: <debug> [1306883794.002657] periodic_update(): Roamed from BSSID 00:25:15:A0:69:76 (SFR WiFi Public) to 00:25:15:4A:95:D2 (SFR WiFi Public) 

```

after this roaming, my ubuntu doesn't reconnect (doesn't even try) to the modem. If i wait a long time, it may connects but i didn't experience it so much. The thing that struggles me is; i don't have this issue when i use my dual windows 7. I didn't follow the system logs in windows but if it disconnects from modem because of romaing, i assume that it reconnects to modem automatically or at least it shows me the login page (i don't have to reconnect to the modem manually). I disconnect from modem when i'm on windows only after my session expires (after 2 hours).

I tried to specify a BSSID in wireless configuration to stick a specific modem but this time ubuntu creates a new wireless connection for the same hotspot and ignores my newly created (bssid specified) connection.

So i have to reconnect manually to the modem everytime it roams and it is really boring. 

Any idea is appreciated. Thanks in advance. 

(i disconnected one more time while writing this post, it happens so frequently)

---

### Post by redmorning on 2011-06-03
bump!

---

### Post by redmorning on 2011-06-23
For about a week or two, i don't have this roaming problem anymore so i think it is not a general issue.

---

