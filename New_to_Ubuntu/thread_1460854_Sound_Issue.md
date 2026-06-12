---
title: "Sound Issue"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by squid68 on 2010-04-23
Using Hardy and having sound issue and not know why. First can only listen to one medium at a time. Cant listen to a song file, cd or streaming audio at the same time anymore. Second I can't stream Sirius radio from the Internet website. Was working fine two days ago and cannot get any sound out of it now. Thanks

---

### Post by I8NY on 2010-04-27
Okay idk what audio driver u r useing but i would move to ALSA.  It fixes a lot of little audio problems for me and maybe for u too.  To get it run```

sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get install alsa-base linux-sound-base alsa-utils
sudo apt-get install gnome-alsamixer 
```
hope this helps.

---

