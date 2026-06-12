---
title: "Sound question"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by augie2051 on 2009-01-10
Does anyone know why my sound is louder and clearer with my Vista than it is with using Alsa Mixer?  The volum control at the same level on both is way louder and clearer with Vista.

---

### Post by 2hot6ft2 on 2009-01-10
Considering 8.10 uses PulseAudio you might start there.
Here are a few options to choose from from fixing pulse to disabling it and using asla, or replacing pulse with esound.

First fixing pulse & system wide EQ
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
A short version here. I suspect it will be modified.
[http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html](http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html)

There are more but this gives you some alternatives that are being used.

---

### Post by unutbu on 2009-01-10
You might also want to open a terminal (Applications>Accessories>Terminal) and type
```

gnome-volume-control 
```
This will launch a program similar to alsa-mixer, but I think more appropriate for Intrepid systems.

Click the Preferences button. Enable everything. Make sure nothing is muted, and then drag the sliders to turn up the volume. 
Pay particular attention to Master and PCM chanels. They both need to be on to hear sound.

---

