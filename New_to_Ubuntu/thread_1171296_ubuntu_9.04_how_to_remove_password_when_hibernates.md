---
title: "ubuntu 9.04 how to remove password when hibernates"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by clownzy on 2009-05-27
I was wondering if someone knows how to remove the need to input my password eveytime my computer goes into hibernation mode.I have managed with help form the forums here to remove it from when I login but I still need to input it everytime it goes into hibernation.
Mnay Thanks

---

### Post by pastalavista on 2009-05-27
Open the gnome configuration editor ```
gconf-editor
```
Navigate to apps->gnome-power-manager->lock and uncheck the "hibernate" box

---

### Post by clownzy on 2009-05-27
Thank you!!!

---

### Post by durand on 2009-05-27
> **pastalavista said:**
> Open the gnome configuration editor ```
gconf-editor
```
Navigate to apps->gnome-power-manager->lock and uncheck the "hibernate" box

Thanks!

---

