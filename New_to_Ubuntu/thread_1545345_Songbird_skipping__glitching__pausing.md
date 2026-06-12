---
title: "Songbird skipping / glitching / pausing"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by hayeled on 2010-08-03
Hi,   I have installed Songbird 1.4.3 on Ubuntu 10.04. It was fine at first (i think, from memory), but it seems to have developed an issue where a song cannot play through without constant tiny pauses throughout the song, every few seconds. Pauses only last for, I don't know, probably less than 50 miliseconds, but it makes listening to music painful.  Has anyone else experienced this, and fixed it?  Cheers.

---

### Post by OriginalName on 2010-08-04
What are your system specs? Could easily be a lack of processing power... mp3 audio takes a bit to decode & could be problematic on an older system... I'd use something like VLC as it's more lightweight...

---

### Post by hayeled on 2010-08-04
It's a Dell Precision 390 Desktop from 2007  Intel Duo Core 2.4 GHz processor 4 GB DDR2 RAM Sigmatel STAC9200 Audio  I've found this thread from a year ago [http://ubuntuforums.org/showthread.php?t=1196209&highlight=songbird](http://ubuntuforums.org/showthread.php?t=1196209&highlight=songbird) which suggests removing pulseaudio.  Is that worth trying? I'm too much of a noob to know if that's even relevant to my situation, whether it may cause further issues, and I wouldn't know how to reinstall pulseaudio if I need to.  I'm pretty committed to songbird because of the auto-lyrics lookup & the functionality mashtape provides. I'd probably surrender ubuntu & go back to windows before abandoning songbird.  God, I hope it doesn't come to that.

---

### Post by hayeled on 2010-08-05
An observation if anyone else ever experiences this issue: If i try to open rhythm box through the main menu, at first attempt it doesn't open. I try again and it does open. Then open songbird. Songbird still skipping. Play a song in both media players, restart songbird, restart rhythmbox, play songs, etc. I've not identified a definite pattern yet, but eventually it stops skipping. At the moment I have both rhythm box & songbird open, I have a song paused in rhythm box, and now songbird is playing mp3s fine - no skipping. It's all a horrible mess. Am i correct in assuming that Ubuntu still isn't "stable" yet? Still a work in progress?

---

### Post by sandyd on 2010-08-05
can you run
```

pulseaudio -k
aplay -l
```
and post the output?

---

### Post by hayeled on 2010-08-05
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]   Subdevices: 0/1   Subdevice #0: subdevice #0

---

### Post by sandyd on 2010-08-06
> **hayeled said:**
> card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]   Subdevices: 0/1   Subdevice #0: subdevice #0

try installing pulseaudio

---

### Post by LowSky on 2010-08-06
> **OriginalName said:**
> What are your system specs? Could easily be a lack of processing power... mp3 audio takes a bit to decode & could be problematic on an older system....

What are you talking about? 

I have played MP3's on my computers since the late 1990's. A 200Mhz computer running Windows 95 can easily play a MP3.

---

### Post by hayeled on 2010-08-06
> **carlee said:**
> try installing pulseaudio

I believe pulseaudio is already installed. Or so ubuntu software centre tells me (it has a lovely green tick). Were you referring to PulseAudio Device Chooser?

I thought I'd just go ahead and install that anyway, but it's refusing to launch. I get a "starting..." notification in the panel, but after a while it vanishes and nothing seems to happen.

The workaround I'm settling for at the moment: open rhythmbox > play any track > pause track > open songbird > songbird plays mp3s as expected.

---

