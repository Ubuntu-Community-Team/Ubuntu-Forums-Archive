---
title: "wooo more sound issues"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by 801TomAK on 2010-03-20
o so sound works fine heres the issue the sound level thing dosnt show up on my desktop and when i go to system preferences sound it fails to load ok it says waiting for sound preference to load or what ever then nothing happens and it disapers

---

### Post by 801TomAK on 2010-03-20
and like it wouldnt be an issue cause i can controll the sound with my speakers but the sound was set pretty low before it stoped working so with my speakers on full blast its pretty quiet

---

### Post by ajgreeny on 2010-03-20
Use the command ```
alsamixer
``` in terminal and ensure that nothing is set too low or muted.  It is, sometimes, the only way to get proper volume levels in Karmic, for some reason.

---

### Post by Enigmapond on 2010-03-20
> **801TomAK said:**
> o so sound works fine heres the issue the sound level thing dosnt show up on my desktop and when i go to system preferences sound it fails to load ok it says waiting for sound preference to load or what ever then nothing happens and it disapers

Sounds like you purged pulseaudio and yes, this will happen when you do that. There are two workarounds.

1) Install gnome-alsamixer and alltray. Open the mixer and alltray together and tell alltray to put the mixer on the upper panel.

or

2) Install either Avant Window Navigator or Docky and add a volume applet to either one of those.

There may be others but these are what I found to get around that Unfortunately when you delete pulseaudio, those are two of the drawbacks.

Good Luck!

---

### Post by 801TomAK on 2010-03-20
alright ill try that and i did find a fix cause to get my sound to work i had to remove pulseaudio but i reinstalled it put the sound back up then i had to remove it again cause my sound got messed up again but yeh its to a point where they system will be loud but i can just use my speakers or what ever to lower the sound

---

