---
title: "Alsa and Creative FX-1"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by johntuck on 2009-03-27
I have now been looking around on the forums for hours and I can't seem to find any kind of answer to my problem. 
I have a Creative FX1 sound card and as many other people are reporting I get no sound. I installed the Creative Sound driver which had the result that I still have no sound and that the only device that is listed is my webcam before I had Alsa and others listed. I followed the instructions in this post [http://opensource.creative.com/soundcard.html#X-FI](http://opensource.creative.com/soundcard.html#X-FI)
I updated the Alsa packages following this threat [http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade](http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade) and I still have no sound.
I frankly don't know what to do any more or what to search for but a Ubuntu without sound is like a car with no wheels.
I really would appreciate any kind of help you want to give me.
Thanks

---

### Post by miegiel on 2009-03-29
> **johntuck said:**
> I installed the Creative Sound driver which had the result that I still have no sound and that the only device that is listed is my webcam before I had Alsa and others listed.

I have zero experience with the FX1, but what list of devices are you talking about here?

And on listing stuf ...
```
lspci
``` Gives a list of the installed and running hardware devices.
```
aplay -l
``` Lists sound devices alsa can use.

If the FX1 isn't in the lspci list, the driver isn't loading.
If it's in the lspci list but not in the aplay list, it's probably alsa.

---

