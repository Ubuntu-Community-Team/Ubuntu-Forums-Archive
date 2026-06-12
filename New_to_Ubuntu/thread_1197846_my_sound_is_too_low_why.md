---
title: "my sound is too low why?"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by heyyy on 2009-06-26
some help to adjust it?

---

### Post by WRDN on 2009-06-26
Try changing the volume settings in the "gnome-volume-control" (type that in the Terminal, press Alt+F2 and type it in, or use another preferred method to run it).

---

### Post by Divider on 2009-06-26
Turn up "front panel" and "PCM / PMC " if it shows up. 

**Hint look for the speaker icon in the top left and double click it. **

---

### Post by kansasnoob on 2009-06-26
Install "gnome-alsamixer" either using Synaptic or go to terminal and run:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video. Pay attention to all toggles but especially the first three and the last four (via) toggles!

---

### Post by heyyy on 2009-06-26
> **WRDN said:**
> Try changing the volume settings in the "gnome-volume-control" (type that in the Terminal, press Alt+F2 and type it in, or use another preferred method to run it).

thanks that helped

---

