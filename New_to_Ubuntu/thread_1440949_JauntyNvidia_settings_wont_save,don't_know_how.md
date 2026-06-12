---
title: "Jaunty:Nvidia settings wont save,don't know how"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by MisFitt on 2010-03-28
Everytime I boot up my screen's set to "auto" and I have to go into the NVIDIA X Server Settings to change the resolution and when I choose to save these settings I'm told it's unable to.Thanks.
The attached screenshot shows:

---

### Post by realzippy on 2010-03-28
Have you run nvidia-settings as root?Try:

```
gksudo nvidia-settings
```

---

### Post by Linuxforall on 2010-03-28
after running nvidia-settings as root, don't forget to save to x for your resolution to stick. Also if you wish to have color settings stick, open up nvidia settings terminal and after setting your color preferences, make a entry in startup applications with command nvidia-settings --load-config-only this will make all your color settings stick next time you reboot.

---

### Post by MisFitt on 2010-03-28
> **realzippy said:**
> Have you run nvidia-settings as root?Try:

```
gksudo nvidia-settings
```
Thankyou so much,worked and now I know how.
I've begun a notebookand this is already written in.
THANKS

---

### Post by MisFitt on 2010-03-28
Thankyou,great tip and in the notebook already!
Cheers and thans for your time,appreciated

---

