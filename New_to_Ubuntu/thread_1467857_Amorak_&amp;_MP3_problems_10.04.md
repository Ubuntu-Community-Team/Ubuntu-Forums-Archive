---
title: "Amorak &amp; MP3 problems 10.04"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by loseby on 2010-05-01
Cant get mp3's to play through Amorak. Have searched and in some answers the threads have been deleted and some may be out of date but I got a recent one and did this

> sudo apt-get install ffmpeg libavcodec-extra-52

but still no sound through Amorak ( yes I have sound elsewhere )

Only reason I want to use Amorak is that the sound in Rythembox or whatevers its called ( I removed it ) sounds tinny as does it in Movie player. I want to add bass but cant get it to work.

---

### Post by mc4man on 2010-05-01
If this is a sound issue don't know ( and I also don't use amarok 2, pana (amarok 1.4) instead), but if it's a decoding issue then make sure this is installed
```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by loseby on 2010-05-01
it shows that 

libxine1-ffmpeg is already the newest version.


am going to try and play some CD's just to be sure  :-)

---

### Post by loseby on 2010-05-01
edit : solved ....dumped Amorak and went with audacious

---

