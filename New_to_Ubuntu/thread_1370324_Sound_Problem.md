---
title: "Sound Problem"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by viladkarab on 2010-01-02
I am having Acer Aspire One 10" Laptop, with Ubuntu 9.04 Installed on it with dual boot Windows XP. I have one problem: - When I suspend the laptop, and again put it on when needed, sound is silent, despite of the volume control slider position. If I shut it off and again log on to Ubuntu, everything works fine. Only after suspending and resuming back, this problem persists. 

Regards. 

Ani

---

### Post by Temposs on 2010-01-02
You might try restarting pulseaudio when you resume. So, you could use this command:

```
sudo /etc/init.d/pulseaudio restart
```

---

### Post by viladkarab on 2010-01-02
I am using HDA (Alta Mixer). Should I change this? and how? I am novice, so pls. guide me accordingly. 

Thanks and Regards.

Viladkarab.

---

