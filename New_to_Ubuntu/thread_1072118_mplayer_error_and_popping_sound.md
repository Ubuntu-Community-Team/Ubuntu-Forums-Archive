---
title: "mplayer error and popping sound"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by ramyy on 2009-02-17
Whenever i play something with mplayer, i get a clicking/popping sound at the very beginning... then the sound works fine..

Its not really a big deal but its annoying..

Also, i get this error when starting a movie:
[ao_alsa] alsa-lib:pcm.c:2196:
(snd_pcm_open_noupdate) Unknown PCM hw:0,1,AESO=6

edit: that popping sound is at the beginning of everything... even when i do the tests on the Sound section, i get that popping sound at the beginning
(I dont think its a problem with he speakers because it worked fine in windows)

---

### Post by ramyy on 2009-02-18
bump, any ideas?

---

### Post by gackt on 2009-02-20
try this:
1. go to preference
2. Select the audio tab
3. choose alsa 
4. configure driver
5. change the device to hw:0,0

---

