---
title: "Can't make speakers work in Jaunty"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by ProginoskesLives on 2009-05-17
After reading many, many threads on how to make my computer's built-in sound card (a Macbook Pro Nvidia one) work with ALSA (which it does not), I gave up and tried to reroute the sound through external speakers.  I have Altec Lansing GCS100 speakers plugged in through the headphone jack, but I don't know how to make Ubuntu recognize that there are speakers plugged in.  I have all the volume on everything turned all the way up, but nothing will play.  Help?

---

### Post by gettinoriginal on 2009-05-18
This solved my problems, good luck  :p
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

---

### Post by skymera on 2009-05-18
I think the sound is very very low by default. Almost muted.

Run ```
 alsamixer 
``` from the terminal and raise the volume manually.

---

