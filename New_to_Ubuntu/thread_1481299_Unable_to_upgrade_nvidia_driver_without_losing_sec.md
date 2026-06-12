---
title: "Unable to upgrade nvidia driver without losing second monitor"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by Captain Carrot on 2010-05-12
That's the gist of it. I have two nvidia graphics drivers options available on the proprietary hardware driver menu, but if I try to activate either, my second monitor bows out. Which means no desktop effects, which I don't *particularly* care about, but i'd at least like to see them.

---

### Post by bodhi.zazen on 2010-05-12
Install the nvidia driver

Reboot

Run ```
gksu nvidia-settings
``` and set your monitors, save your settings.

---

### Post by Captain Carrot on 2010-05-12
From the terminal I presume? I didn't get any result. Checked monitors in preferences and the second still isn't being recognized.

---

### Post by bodhi.zazen on 2010-05-12
Is nvidia-settings installed ?

```
sudo apt-get install nvidia-settings
```

---

### Post by Captain Carrot on 2010-05-12
That would be it, thank you! It was agony. Required extensive googling, an unsolicited hard disk check, 10 restarts, a still no doubt corrupted nvidia config file and me somehow getting my mouse trapped on the wrong monitor, but my windows now wobble gratifyingly when I move them about.

---

