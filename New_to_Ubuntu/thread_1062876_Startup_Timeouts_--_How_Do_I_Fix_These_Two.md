---
title: "Startup Timeouts -- How Do I Fix These Two?"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by JamesV on 2009-02-07
My desktop is slow to load. Looking at the system log, I found two 10-second timeouts. If I could fix these, that would shave 20 seconds off of my startup time. 

```

Feb  7 07:34:42 ubuntu x-session-manager[6084]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Feb  7 07:34:52 ubuntu x-session-manager[6084]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 

```

So, where do I start to track these down and fix them? Ubuntu 8.10, GNOME 2.24.1

---

### Post by ptn107 on 2009-02-07
It is a known bug for some, which only has a temporary fix right now.  You need to go into System -> Preferences -> Appearance.  Click the 'visual effects' tab and set to 'none'.  Restart.

---

