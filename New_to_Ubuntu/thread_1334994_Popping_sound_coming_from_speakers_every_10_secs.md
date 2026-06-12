---
title: "Popping sound coming from speakers every 10 secs"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Pwhdavey on 2009-11-23
Since I have installed Ubuntu today there has been a 'popping' sound coming from the speakers of my laptop when I am on Ubuntu. Like the sound of when you connect headphones or something to their port. It happens every 10 seconds. I have my sound on mute but the sound still goes, with or without earphones connected. How can I stop it?

---

### Post by wojox on 2009-11-23
Try:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Look at the bottom for:

options snd-hda-intel power_save=10 power_save_controller=N

and uncomment it.

---

