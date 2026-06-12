---
title: "More NVidia Problems"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Spiritous on 2009-04-25
I keep setting NVidia to use my two PC screens (Dell + Phillps), Whenever i restart the PC, it goes back to one screen, my dell and i have to reconfig

---

### Post by stretch427 on 2009-05-13
It might be a problem with permissions 
```
sudo nvidia-settings
```
then configure and save and you should be good. I apologise if you've already fixed the problem.
Cheers!

---

### Post by donaldt on 2009-05-15
I have been fighting that problem for weeks.  You were correct.  Permissions cured the problem.  I just had to log on as root and the screen resolutions (both) worked!

thanks,

donaldt

---

### Post by stretch427 on 2009-05-16
No problem! Glad to be of assistance.

Stretch

---

