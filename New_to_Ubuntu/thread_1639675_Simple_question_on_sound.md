---
title: "Simple question on sound"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by oldmankit on 2010-12-07
Does Ubuntu 10.10 come with ALSA or pulse-audio as default?


I've found projectM visualisations and am loving them.  At the moment they're only working when I crank up JACK and use projectM-jack.

There is a package called projectM-pulseaudio, but when I run this it doesn't seem to be picking up any of the sound from VLC.  I can't seem to find out if VLC is using ALSA or pulse-audio.  The default output is set to jack, but I don't know what it falls back on when I don't have JACK running.

---

### Post by NightwishFan on 2010-12-07
Ubuntu has pulseaudio installed by default. I believe anything with alsa is automatically re-routed through pulse. (However I could be wrong).

---

### Post by oldmankit on 2010-12-07
So that means there's probably a problem with my projectM-pulseaudio.  I'll look into why it's not picking up the sound from VLC.

Thanks.

---

