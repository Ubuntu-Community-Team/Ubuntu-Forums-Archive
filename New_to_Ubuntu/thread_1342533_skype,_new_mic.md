---
title: "skype, new mic"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by mastermael on 2009-11-30
I know that skype is a big issue, i am running jaunty. When i try to call i get error message "problem with audio playback" is there an easy way to fix this.

---

### Post by HermanAB on 2009-11-30
In the Skype sound configuration menu (main menu, options, sound devices) set all three sound devices to something like /dev/dsp or /dev/dsp1 (if it exists) and tick the box to let Skype manage the volume, then test it. 

If you have trouble, get the 'Static' version of Skype:
[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)
(the last download option)

---

### Post by mastermael on 2009-12-01
Thanks, changing to static did the trick.

---

### Post by mastermael on 2009-12-03
Static stopped working, i didnt change anything. And im getting "problem with audio playback" again, any help?

---

### Post by mastermael on 2009-12-03
I fussed around a little, Now i can make calls, I just can't hear the other person. Any help?

---

### Post by mastermael on 2009-12-03
bump

---

### Post by spiderbatdad on 2009-12-03
I use version 2.0.0.72 and set both in and out in sound devices to pulse.

---

### Post by mikewhatever on 2009-12-03
Please don't bump every 30 minutes. You need to open Skype's audio settings, and change the output device (or speakers) to something other then the default. Pulseaudio or alsa may be a good choice.
What does 'skype,new mic' has to do with your problem? If you want fast help, at least think up a decent thread title.

---

### Post by mastermael on 2009-12-03
My problem is: I cannot hear the other person speak, I do not know if they can hear me.

---

