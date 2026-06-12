---
title: "How to set up nvidia sttings manager to start at maximum performance at startup"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by hovzio on 2010-11-27
Compiz lags for a second or two when my graphic card is set on adaptive, hence I set it to max performance within the nvidia settings. This does the trick and works great, the problem is that every time i reboot this is set back to adaptive; does anyone know how to make this setting permanent? Thanks:D

---

### Post by wojox on 2010-11-28
Have you tried setting it as root:

```
gksudo nvidia-settings
```

---

