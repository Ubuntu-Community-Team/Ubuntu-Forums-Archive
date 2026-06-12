---
title: "Disable wireless?"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by Sporkmaster on 2007-07-19
My laptop has a wireless antenna built in, but I use wired connection now. Wireless was too much of a pain. How can I stop it from randomly connecting to my neighbor's networks?

---

### Post by djdicbob on 2007-07-21
Find out what driver module loads for the wifi and append...

```
blacklist *modulename*
```


to the file **blacklist** in the** /etc/modprobe.d** directory:)

---

