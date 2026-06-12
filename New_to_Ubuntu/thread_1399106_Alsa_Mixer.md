---
title: "Alsa Mixer"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Optimust on 2010-02-05
I'm working with 8.04, Hardy on a Lenovo 3000 N200.  Yes I know they're both old  : )

I got sound working through archived threads and need to mute the microphone through ALSA mixer to stop feedback.  I "muted" it in terminal but it's still on.   I feel silly but for the life of me I can't find the ALSA GUI mixing board with all my poking around.  

Is there an application reinstall I need?  By all comments it should be simple but I don't find it. . .

Cheers

---

### Post by SuperSonic4 on 2010-02-05
I'm not sure what it is in Gnome (it's kmix in kde) but you can always open up a terminal and type *alsamixer*

F6 is change sound card and Esc is exit

---

### Post by jmszr on 2010-02-05
Optimust,

Or you can

```
sudo apt-get install alsamixergui
```

which then can be found under Applications > Sound & Video.

---

