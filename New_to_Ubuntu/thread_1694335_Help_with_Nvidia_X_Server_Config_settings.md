---
title: "Help with Nvidia X Server Config settings"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by jermza on 2011-02-24
I've searched Google for some simple user guides to using the Nvidia X Server settings, but I'm struggling to find much.

Apologies if I seem ignorant.  What I want to do is to enhance the performance of my graphics card, so that things render / animate a bit more smoothly etc. 

Which options should I adjust to achieve this?  If you've played with these settings, then how have you tweaked them?

---

### Post by LowSky on 2011-02-24
What model video card do you have? What issues are running into that it needs adjusting?

Just mess with the OpenGL setting slider and dont forget to open nvidia-settings with sudo access so the settings actually works
```
gksu nvidia-settings
```

---

