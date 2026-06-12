---
title: "Command line to access wifi"
date: 2019-03-19
forum: Networking &amp; Wireless
---

### Post by jimhce on 2019-03-19
Hi,

Is there any command line to check wifi status? I am not running network manager, so cannot use nmcli. I am running connman, it cannot scan the wifi due to the wifi is not switched on.

Thank you.

Kind regards,

- jh

---

### Post by kc1di on 2019-03-19
if your wifi is switched off you can try this command and see if it will turn on```
rfkill unblock all
```

---

