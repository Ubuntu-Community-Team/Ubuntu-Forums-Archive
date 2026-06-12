---
title: "KVIRC icon not in tray"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by fritz269 on 2011-05-24
So I installed the 11.04 64-bit version and I cannot get kvirc icon on the sytem tray next to the time to show up, I had it working before moving to 64 bit. Also, every time I go and start it, it goes through the whole initial set up asking me for user name. 

The most annoying thing is that when I close or minimize the tray and try to start it again, it tells me that there is already a session running. Anyone help?

---

### Post by fritz269 on 2011-06-03
OK. so I was able to fix the tray notifications by using this code

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

Then logged out and logged back in.
Found it at this location that was stickied in the General Help Section
[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

