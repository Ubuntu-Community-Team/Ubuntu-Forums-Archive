---
title: "No sound in mplayer/totemplayer"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by ashwat on 2009-03-15
After installing quite a few programs to get back upto speed, there is no sound from players based on totem or mplayer. Skype works fine and so does Flash in firefox. PCM is on full on Alsamixer.

---

### Post by earthpigg on 2009-03-15
tried killing pulse audio and then running the apps?

```
grep -A | pulse
```

that will return a number.

```
kill -9 thatnumber
```

ie: ```
kill -9 12345
```

---

### Post by ashwat on 2009-03-15
trying autodetect worked after a few tries. I'll try what u have suggested if I come across with this problem again.

---

