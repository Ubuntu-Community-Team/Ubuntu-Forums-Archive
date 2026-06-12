---
title: "ALSA or PulseAudio... which to use?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by egalvan on 2009-02-09
I am just starting to get into the audio stuff under Ubuntu...
Under hardy 8.04.x
-----

ALSA or PulsAudio.

Questions:

Which to use?

which has more support by audio programs?

Which is "better"
Why?

Is one preferred under Gnome or KDE?


I google'd this stuff, and searched on this forum, but I am overwhelmed.

Ernest

---

### Post by kansasnoob on 2009-02-09
You really have no choice:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Really!

---

### Post by mc4man on 2009-02-09
> You really have no choice:

You are free to choose in both 8.04 and 8.10 if you want to use pulse or not.

In 8.04 the implementation is poor, the above link will help to set up properly. Once set up pulse does work very well in most cases, particularly if you use gstreamer apps.

If you choose not to use it (based on performance, sound quality, your sound system, and the apps you use) it's usually only a matter of switching your sound settings from 'default' or 'pulseaudio' to alsa. (system wide and or in your apps settings.

It works much better in 8.10, but again in some cases it's better without. In 8.10 though, pulseaudio must be removed as completely as possible, depending on what plugin's you want, libpulse0 may need to stay (it's presence won't be a negative


In 2 set ups with very good 5.1 sound systems and a compare test with a borrowed high end 5.1 system (analog) on 8.10, when using amarok, audacious, vlc and mplayer,  overall, 'alsa only' provided the best combo of sound quality, performance and cpu usage. ( in terms of direct playback of a variety of audio sources, not accounting for or considering any of the more 'exotic' uses of pulseaudio

---

### Post by binbash on 2009-02-09
At 8.10 pulseaudio is getting better and better but sometimes it causes bugs or crashes at some games/applications.I usually choose alsa

---

