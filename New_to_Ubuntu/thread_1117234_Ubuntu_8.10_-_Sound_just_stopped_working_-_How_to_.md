---
title: "Ubuntu 8.10 - Sound just stopped working - How to fix it?"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by swarup on 2009-04-05
Yesterday I installed Ubuntu 8.10 in my Dell E520 desktop. The sound was working perfectly fine. Today I installed a transcription program from NCH called "Express Scribe". They have a linux version of the program. I was using the program to listen to an mp3 sound file, and was adjusting the playback speed. In the process of doing so, all of a sudden the sound became like a feedback sound. And since then, even after reboot there is no sound at all in any of Ubuntu's sound software (Movie Player, Rhythmbox, etc). How can I get my sound back?

---

### Post by UbuntuNerd on 2009-04-16
try the Comprehensive Sound Problem Solutions Guide from the forum:
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by fro1269 on 2009-04-17
> **swarup said:**
> Yesterday I installed Ubuntu 8.10 in my Dell E520 desktop. The sound was working perfectly fine. Today I installed a transcription program from NCH called "Express Scribe". They have a linux version of the program. I was using the program to listen to an mp3 sound file, and was adjusting the playback speed. In the process of doing so, all of a sudden the sound became like a feedback sound. And since then, even after reboot there is no sound at all in any of Ubuntu's sound software (Movie Player, Rhythmbox, etc). How can I get my sound back?


try 

```
sudo killall pulseaudio

sudo alsa force-reload
```



and then go to System>Preferences>Sound and change everything to ALSA

---

### Post by Crusty Juggler on 2009-04-17
Same thing happened to me on a Toshiba Satellite A300.  One day, sound is fine, next day, all I get is crackling when sounds should be playing.  Switching to OSS allowed for test beeps to be heard, but under alsamixer, the only option available was "main," so I couldn't use headphones or anything.

If you're planning on upgrading to Jaunty anyway, do what I did and dl the release candidate now and install it.  Your sound will be fixed, a lot of other niggling issues I had (i.e. bluetooth) were fixed and you get to avoid the crush of people downloading on the release day.

---

