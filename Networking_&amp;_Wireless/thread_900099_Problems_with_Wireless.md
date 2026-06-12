---
title: "Problems with Wireless"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by nerkel on 2008-08-25
I am a new Ubuntu convert, so forgive me if I don't know much. My friend, who showed me Ubuntu, helped me alot.

I attempted to install the driver for my wireless chip through the restricted drivers manager and it made my machine nearly unresponsive even though the CPU is in idle.

I'm using a BCM4318 and even attempts to install the driver and firmware through several guides on the wiki and here on the forum had the same result after clean installs.

any ideas to get this wireless chip working?

---

### Post by Crafty Kisses on 2008-08-25
Post these outputs:
```
ifconfig
```
Then:
```
lshw -C network
```

---

