---
title: "No sound Firefox/Rhytmbox, yes on other progs."
date: 2009-05-25
forum: New to Ubuntu
---

### Post by Omualdo on 2009-05-25
I have a problem with sound. One day I couldn't listen anything in the headphones jack. I fixed it somehow (although I still have this problem every now and then). Ever since I got that fixed I have this problem:

I can listen to it via Firefox, Totem, Rhytmbox and Banshee (although this last two show the playlist and when I try to play a song it will show me as if there was no archive supporting that song and thus going like this in all my playlist... I don't know if it's the same problem, but it started at the same time).

I have no problem with Audacious, Amarok or VLC.

Help? Thanks!

---

### Post by Omualdo on 2009-05-26
anyone?

---

### Post by Sarai the Geek on 2009-05-26
I don't know a whole lot about audio issues, but you might get more help if you provide a bit more information. Post the output of these two commands:

```
lspci | grep Audio
```
and
```
cat /proc/asound/card0/codec#* | grep Codec
```

---

