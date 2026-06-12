---
title: "can not get any audio, please help"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by killbydemons on 2009-01-05
I've been trying to fix this for several hours now, and I'm at the point where I'm likely to blame Ubuntu for the problem.  Somebody please tell me I'm wrong.

I know that Ubuntu detects my audio processing device (happens to be onboard), which is AC'97.  Following a guide on these forums led me to try and load the snd-intel8x0 module, which is the one I need for my sound card.  Loading the module does nothing; no audio from youtube, nothing from music cds.  Any help at all? Does everyone get this problem when they install Ubuntu for the first time?

---

### Post by jbrown96 on 2009-01-05
Try changing your playback device to Alsa. In System-->preferences-->sound. Then use the test button. If that still doesn't work, try to adjust each channel's volume. In a terminal use, ```
alsamixer
``` If you try unmuting a channel and increasing its volume, but it doesn't work, mute it again because it may cause static when you get it working.

---

### Post by 2hot6ft2 on 2009-01-05
Do you have all the needed codecs to be able to play sound?
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Or the short way

```
sudo apt-get install ubuntu-restricted-extras
```

in a terminal.
Applications>Accessories>Terminal
When it gets to the agreement hit Tab then Enter to accept the Java agreement.

8.10 uses PulseAudio
Here are a few options to choose from from fixing pulse to disabling it and using asla, or replacing pulse with esound.

First fixing pulse
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

### Post by killbydemons on 2009-01-06
thanks guys, I'll try those to fix the audio.

---

