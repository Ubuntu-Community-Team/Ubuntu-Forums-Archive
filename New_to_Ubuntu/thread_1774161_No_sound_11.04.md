---
title: "No sound? 11.04"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by Proto Blaze on 2011-06-02
So I just installed 11.04 and did what I normally do to get the features... but the sound doesnt work... any ideas? (i switched to the classic UI)

---

### Post by wolfen69 on 2011-06-02
Do:
```
alsamixer
```
and check your settings.

---

### Post by Proto Blaze on 2011-06-02
> **wolfen69 said:**
> Do:
```
alsamixer
```and check your settings.

 ok i did that.... now what do i do with it?  EDIT: I figured it out... and omg its midnight and i had my speakers shooting screamo.... scared me bad!!!

---

### Post by CunningGoose on 2011-06-03
> **Proto Blaze said:**
> ok i did that.... now what do i do with it?
 
Does your soundcard show up when you hit F6? Scroll down with the arrow keys, select it and check the volume settings. For some reason for me when I first installed, the master volume was set to a goose egg on it.
 
Also can check under system preferences under sound for what your output device is. Mine defaulted to my HDMI output attached to my monitor, no sound was going there but it thought it would go there anyways.
 
Combo of these two spots fixed my problem :)

---

