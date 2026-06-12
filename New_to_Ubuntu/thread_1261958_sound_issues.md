---
title: "sound issues"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by jabbathehinds on 2009-09-09
Can someone please help me figure out why the sound on my computer is so low?
Yes, the volume is up, haha. It's just really quiet.
I'm using UNR 9.04 on an Asus Eee PC.
Thanks in advance!

---

### Post by NightwishFan on 2009-09-09
Open a terminal (Applications -> Accessories -> Terminal) Type this command and press enter.

```
alsamixer -c0
```
That is a 0 as in 1001100110, not an "O"

It should list your sound card mixers, one of the main culprits for low volume is PCM.

---

### Post by jabbathehinds on 2009-09-09
Thank you so much! I just made the leap from windows, and I'm still finding my way around. At least now I can enjoy my music.

---

### Post by NightwishFan on 2009-09-09
Glad you got it working. Sometimes PCM goes quiet, but that solution, or the volume mixer in the panel can fix it. Do not worry, Linux compatibility only gets better as time goes on. Enjoy using Ubuntu, and good luck.

---

### Post by jabbathehinds on 2009-09-09
Oh and that Ubuntu Tutorials link is exactly what I needed!
Thanks again.

---

