---
title: "Alsamixer speaker showing 0"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by LittleGyko on 2010-07-12
hi,

after installing ubuntu 10.04, i upgraded from alsa 1.0.21 to 1.0.23. the sound quality seems to be very bad now. 

when i use alsamixer, the speakers are at 0 and i am not able to increase them.

can someone please help?

thanks

---

### Post by fooman on 2010-07-12
there is a nice gui version of alsamixer you could try....might be a little easier to use.

install with synaptic (system > administration > synaptic package manager) and search for/install "gnome-alsamixer",  or open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
sudo apt-get install gnome-alsamixer
```

after it installs,  find it in: applications > sound and video > gnome alsa mixer.

see if you can adjust the volume there.

hope that helps.

---

### Post by LittleGyko on 2010-07-12
gnome alsamixer shows everything is full. but alsamixer again shows speaker 0. this is strange!

---

### Post by fooman on 2010-07-12
> **LittleGyko said:**
> gnome alsamixer shows everything is full. but alsamixer again shows speaker 0. this is strange!

in gnome alsa mixer...there are boxes for "mute" under each slider,  make sure they are not checked.

also,  have you left-clicked on the speaker icon that is in the top panel?  there should be a volume slider there (make sure it is turned up and that "mute" is not selected).  you should also see "sound preferences" there.  click on that and see that the volume slider is up and mute is not checked.

---

### Post by LittleGyko on 2010-07-12
i checked all that and i guess everything is fine. maybe that the sound is bad was only my imagination! thanks anyway!

---

