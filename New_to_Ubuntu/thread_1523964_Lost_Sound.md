---
title: "Lost Sound"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by alpinescrambler on 2010-07-04
Since one time when I muted my sound and re-booted my computer, I have no sound, even after I tuned the sound back on.  I read various threads and tried setting the volume, changing the settings and so on, but can't get the sound back.

It SAYS full volume, but I'm getting nothing.

Any suggestions?

---

### Post by alpinescrambler on 2010-07-05
bumpy.

---

### Post by alpinescrambler on 2010-07-05
Actually, after trying everything I've read on this forum from the last few months, I'm beginning to suspect my sound card has died.  I've ordered another one.  Let's see if that works.

---

### Post by lidex on 2010-07-07
If you dual-boot windows, try adjusting in windows. Now reboot into ubuntu. Result? No help, try this:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

