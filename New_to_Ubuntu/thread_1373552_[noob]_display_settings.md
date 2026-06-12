---
title: "[noob] display settings"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Intell on 2010-01-05
[IMG]http://imgur.com/nAJUv.jpg[/IMG]
Display was working until I set the resolution wrong once.
Log in screen displays fine, until I log in.

Graphics card details:
GeForce4 FX5200XT (Lancer)
AGP 8x graphic card
128MB maximum DDR video memory 

I tried the recovery mode video fixer and dpkg reconfigure.

What next?

---

### Post by jonest1 on 2010-01-05
I came across the nvidia-xconfig command, if you're using the nvidia driver.  You can google it for information.

I believe you may be interested in something similar to the following.
```
nvidia-xconfig --mode=1280x1024
```

I hope this helps.  Please post a reply if you're still having problems.

---

