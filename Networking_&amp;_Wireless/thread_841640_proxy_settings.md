---
title: "proxy settings"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by Okar on 2008-06-26
Hi, 
under System->Preferences->NetworkProxy
you can set the global proxy settings.
can they be set somehow automatically through a script or a program?
I hope you know a solution.

---

### Post by chewearn on 2008-06-27
The proxy settings are held in gconf > /system/proxy.  You can use gconftool-2 to change the setting via script.

E.g. to turn proxy from none to auto:
```
gconftool-2 -s -t string /system/proxy/mode auto
```

And turn it back:
```
gconftool-2 -s -t string /system/proxy/mode none
```

---

