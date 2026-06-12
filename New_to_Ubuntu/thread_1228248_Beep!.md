---
title: "Beep!"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by Hoom@n on 2009-07-31
1-When I shut the computer down, I hear beeps several times! That are too loud and unnecessary[in my opinion]! Is there any problem, or it's normal? / How can I get rid of it?
2-When I use up/down/left/right in a text-area, if I reach the first/end of the text I here a loud beep! How can I make it lighter?!

---

### Post by Liolikas on 2009-07-31
```

alsamixer

```
(If Ubuntu has it) or other mixer should allow to mute it.

---

### Post by mprince on 2009-07-31
Also, check for the *Preferences>Sound>System Beep tab*.

---

### Post by lisati on 2009-07-31
Beeps from the computer's speaker upon shutdown have been reported in the forums before...... now where did I hide that link?

---

### Post by wojox on 2009-07-31
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

And add this

blacklist pcspkr

At the end of the file.

---

