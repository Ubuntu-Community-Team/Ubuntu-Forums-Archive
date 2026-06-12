---
title: "how to save xconfig for nvidia"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by JamesMcG on 2009-01-31
I had to reinstall OS, I have a dual monitor configuration. I remember that when I set it up the first time. I had to use the terminal and use sudo to launch a program to get the xserver to allow me to config it properly. Unfortunately, I don't remember what command I used. I'm running an nvidia card, I have the driver installed already.

Thank you,
Jim

---

### Post by Crafty Kisses on 2009-01-31
Not sure what you're asking, but you can access your X by running the following command:
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by jimmy the saint on 2009-01-31
I think you are looking for
```
gksudo nvidia-settings
```

---

### Post by JamesMcG on 2009-01-31
Sorry stepped away for dinner. Yes the gksudo nvidia-settings was it.
Thank you, I knew it was simple but couldn't remember the command for the life of me.

Thank you,
Jim

---

