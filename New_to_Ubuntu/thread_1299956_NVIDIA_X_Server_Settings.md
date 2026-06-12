---
title: "NVIDIA X Server Settings"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by pkjm17 on 2009-10-24
I can't seem to save the changes I want for my display. I want a 1680x1050 screen resolution, so I apply it, but then when I click on "Save to X Configuration File", and click save, it says "Unable to create X config backup file '/etc/X11/xorg.conf.backup'."

---

### Post by Arup on 2009-10-24
In terminal do a gksudo nvidia-settings

---

### Post by SuperSonic4 on 2009-10-24
Run nvidia-settings as root

```
gksu nvidia-settings
```

---

