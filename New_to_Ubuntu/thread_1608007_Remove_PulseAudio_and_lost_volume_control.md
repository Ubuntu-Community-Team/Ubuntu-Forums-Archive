---
title: "Remove PulseAudio and lost volume control"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by beew on 2010-10-28
Hi,

I am running Maverick in an old machine (512Mb) and av performance is kind of problematic.  I managed to get a quite significant improvement by removing pulseaudio and installing alsa. Now the problem is the volume control has disappeared and on clicking system > preference > sound I get a pop up box that says "waiting for sound system to respond". So I can only adjust audio or video volume only through the player. How do I fix this?

Otherwise I have no problem in audio and video playback , in fact it gets a lot smoother.

---

### Post by alexandari on 2010-10-28
It probably removed the pulseaudio volume control too...if you want it back,

```
sudo apt-get install pavucontrol
```  (But I dont think you do)

check this out [http://ubuntuforums.org/showthread.php?p=10008815](http://ubuntuforums.org/showthread.php?p=10008815)

---

