---
title: "Gnome-sound-properties and non autodetect on devices"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-07-13
Hi guys I have this issue that I cant play 2 sounds at once, I fixed this by going to system>preferences>sound>devices and turn everything to ALSA(default was autodetect) the real problem is, how do I go into a config file and change that, because on my live cd it will always default on auto default, anyone know the config file for system>preferences>sound>devices?

---

### Post by ericeclifford on 2009-07-13
anyone got any ideas?

---

### Post by DaGrimReefah on 2009-07-13
Try 

```
killall pulseaudio
```

in a terminal. You can add it as a start-up script as well.

---

### Post by ericeclifford on 2009-07-13
it worked on my harddrive install, I put it in my astartscript for my live cd customization, see if it will work, PS ty.

---

### Post by ericeclifford on 2009-07-14
Still does not work, I put sudo killall pulseaudio in my startup script and two sounds at once still couldn't play, is there a config file for this fix or not?

---

