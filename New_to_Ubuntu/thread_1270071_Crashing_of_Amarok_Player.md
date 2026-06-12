---
title: "Crashing of Amarok Player"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by nns2006 on 2009-09-19
hi,
I have installed KDE 4.3 desktop and i love it. But my problem is when i want to use Amarok player. It says that some restricted updates has to be downloaded.It downloads the updates successfully but while installing it crashes. What to do?
Thanks in advance

---

### Post by mc4man on 2009-09-19
Don't have kde, am actually using 8.04 w/gnome, so don't know why you're crashing.

Anyway, what amarok probably needs is libxine1-ffmpeg so maybe just try installing it yourself and see what happens

```
sudo apt-get install libxine1-ffmpeg
```

Amarok (at least 1.4) can also use w32codecs on a 32bit install. If needed then get from medibuntu

---

### Post by nns2006 on 2009-09-19
Restricted updates are
1.mp3 tag reading
2.video codec
3.MPEG plugins

---

