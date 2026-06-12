---
title: "Virtualbox resolution problems"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by wrtpeeps on 2011-06-21
So I just installed 11.04 in virtualbox, however I can't pick a resolution above 800x600. I've tried installing the guest tools and it still doesn't give me the option of a higher resolution when I go to System > Preferences > Monitors.

What else do I need to do?

---

### Post by mikenev on 2011-06-21
You should only have to install the tools to get higher resolutions. Did you give the VM enough video RAM? 16MB should be enough for most screens. Did you restart X or reboot the machine after installing the tools?

---

### Post by wrtpeeps on 2011-06-21
Got it sorted. Apparently it only lets you pick a higher res if you have it in full screen mode.

---

