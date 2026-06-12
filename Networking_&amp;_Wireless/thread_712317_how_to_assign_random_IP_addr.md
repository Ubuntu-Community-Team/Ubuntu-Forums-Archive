---
title: "how to assign random IP addr?"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by coreSOLO on 2008-03-01
I want to assign random IP address to my interface wlan0 within a range say 192.168.0.1 to 0.100 then how do I do this? Right now i am using "ifconfig wlan0 192.168.0.10 up"...

---

### Post by The Cog on 2008-03-01
A script like this might do it:
```
#!/usr/bin/python
import random, os
r = random.randint(1,100)
s = "ifconfig wlan0 192.168.0.%s up" % r
os.system(s)
```

---

