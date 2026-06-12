---
title: "Modem off/on, no Internet..."
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by TenPlus1 on 2007-09-24
I've noticed that when my cable modem is turned off then back on again, my internet connection stays lost until I reboot Ubuntu...

Is their a shortcut to re-enable my internet connection ?

---

### Post by noob12 on 2007-09-24
It depends on how you connect.

In the most common cases, this should do it:

```
sudo /etc/init.d/networking restart
```

---

