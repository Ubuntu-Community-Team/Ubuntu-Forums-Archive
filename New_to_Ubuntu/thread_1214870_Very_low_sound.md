---
title: "Very low sound"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by Gusx1 on 2009-07-16
Well, it seems Ubuntu has extremely low sound compared to Windows. Is there anyway i can improve my sound? I'm unsure of my sound card honestly. My slider on my speakers is in the middle, i could have halfway from the bottom and i could hear it excellent, is there anyway too improve the sound? Or is alsa mixer just bad?

---

### Post by NightwishFan on 2009-07-16
Try this command to see if all your sliders are correct.

```
alsamixer -c0
```

Then make sure pulse sliders are correct, and they should be.

---

### Post by ubudog on 2009-07-16
Try turning up PCM a little.

---

### Post by Gusx1 on 2009-07-16
I tried the command, and they are all correct. Andd PCM is full blast, everything is, i don't understand whats wrong?

---

### Post by bruce2000 on 2009-07-16
You could try Gnome Alsa Mixer to raise the volume, it made a big difference on my desktop pc.

To install:

```

sudo apt-get install gnome-alsamixer

```

Its menu is in Applications/Sound&Video

---

### Post by NightwishFan on 2009-07-17
The only thing I can think of is Pulseaudio is low. Perhaps install the Pulseaudio volume control, and see what is up. Sound on my PC seems a bit low as well (when maxed), but not unreasonably so.

---

