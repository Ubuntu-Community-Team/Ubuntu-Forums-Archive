---
title: "configuring wireless connection"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by setanta1 on 2008-09-23
hi i am a newbie. i tried to connect to my wireless broadband using  
network tools and there was an option for eth0 which is a cable connection. i needed an eth1 option for wireless but it was missing.
has anybody had this problem?

---

### Post by nixscripter on 2008-09-23
You probably don't have a driver for the card installed. Run the output of this command to see if the card can be identified:

```
lshw -C network
```

---

