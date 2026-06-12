---
title: "How do i play DVDs?"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by leinad177 on 2010-03-12
i installed mplayer and kmplayer and i can't play dvds on them...

i also tried the player that comes with gnome and that didnt work

i haven't updated my ubuntu yet because i have really slow internet thanks to my ISP
(its 64kbps)

can anyone tell me what i need to do?

---

### Post by karthick87 on 2010-03-12
Try **VLC** player
[B]
```
sudo apt-get install vlc
```[/B]

---

### Post by marshmallow1304 on 2010-03-12
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by bcbc on 2010-03-12
[https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html)

---

### Post by bug67 on 2010-03-12
Software Center > Restricted Extras

---

### Post by NightwishFan on 2010-03-12
You need capable codecs to decode DVDs such as ac3 and mpeg2, as well as dvdread and libdvdcss. The link above should tell you how to install libdvdcss, the rest is automatic if you try to play in vlc or totem.

---

### Post by Yanno on 2010-03-12
try Smplayer...

---

### Post by NightwishFan on 2010-03-12
It is not really an issue of the player. It is just the the repositories do not contain libdvdcss, so you have to install it manually from medibuntu.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Disclaimer: Use of this can be considered illegal in some places.

---

