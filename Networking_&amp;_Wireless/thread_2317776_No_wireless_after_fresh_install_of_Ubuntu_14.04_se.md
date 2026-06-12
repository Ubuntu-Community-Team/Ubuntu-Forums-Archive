---
title: "No wireless after fresh install of Ubuntu 14.04 server on Gigabyte laptop"
date: 2016-03-19
forum: Networking &amp; Wireless
---

### Post by SameG on 2016-03-19
Freshly installed Ubuntu 14.04 server on Gigabyte laptop. Connected to wireless fine during the installation process, but now there's no connection.

Wireless is an AR9285. Both wireless and ethernet show as *-network DISABLED.

Could someone show me how to fix this please?

---

### Post by jeremy31 on 2016-03-19
Post the results from ```
rfkill list all; ifconfig
```

---

