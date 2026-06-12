---
title: "Sound mixer missing?"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by farkinid on 2009-12-11
Hi, I've been looking around the system and google but I can't seem to find a way to change my sound settings. I'm currently using 9.10. When I click the speaker icon on the top right of the screen, all it shows is a master volume bar. If I use preferences, I still don't get any other options.

I'm looking for a way to fine tune my volume. In Windows (I'm sorry to use this example), I have a WAV or WAVE slider to manipulate. I'm looking for something equivalent. Any ideas?

---

### Post by FreewheelinFrank on 2009-12-11
Have you tried Pulse Audio Volume Control in Applications>Sound&Video?

---

### Post by farkinid on 2009-12-11
Hmm Pulse Audio Volume Control you say? No such option in my application section

---

### Post by FreewheelinFrank on 2009-12-11
Maybe I had to install it.

Have a look in Synaptic.

---

### Post by muteXe on 2009-12-11
I could be wrong here, but i got some kind of gui mixer type control after installing "ubuntu-restricted-extras" package.  As i said i could be wrong, but spotetd this volume controller thing straight after installing that.

mute

---

### Post by cartisdm on 2009-12-11
Try installing the GUI alsamixer

Type:
```
sudo apt-get install gnome-alsamixer
```

---

