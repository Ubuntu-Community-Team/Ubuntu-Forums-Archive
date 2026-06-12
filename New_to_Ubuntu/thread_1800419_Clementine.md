---
title: "Clementine"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by hifly1231 on 2011-07-08
Anybody know how to get Clementine to play through a USB headset instead of speakers?  I'm clicking on "Devices" in the sidebar, but nothing seems to be showing up for me to choose from.  Any help would be greatly appreciated.  Thanks!!!:D

---

### Post by dcsoldschool53 on 2011-07-08
> **hifly1231 said:**
> Anybody know how to get Clementine to play through a USB headset instead of speakers?  I'm clicking on "Devices" in the sidebar, but nothing seems to be showing up for me to choose from.  Any help would be greatly appreciated.  Thanks!!!:D

Did you try going through your sound preference in System > Preferences to change the speakers to headset.
The Device in Clementine is for an ipod or something like that I think.

---

### Post by hifly1231 on 2011-07-09
I found the answer.  Go to Tools > Preferences > Playback.  Where it says "Gstreamer Audio Engine", choose "Audio Sink (ALSA) from the drop down.  In the box below, input "plughw:Headset,0".  Clementine will then play through your USB headset. :D

---

