---
title: "Best Nvidia soundcard for Ubuntu 9.10 Karmic Koala?"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by tweety_r78 on 2010-02-05
I have a version of Nvidia driver installed, but when I tried to activate it, the screen went oversized (compared to the monitor). I've gotten a tip on a Nvidia with an overscan option..
Anyone know where to download it?

---

### Post by cariboo on 2010-02-06
If you are running Karmic (9.10), start in recovery mode, and select drop to root prompt, once at the prompt type:

```
nvidia-xconfig
```

This will create a new /etc/X11/xorg.conf file, once the file has been created type reboot at the prompt to restart your computer.

---

