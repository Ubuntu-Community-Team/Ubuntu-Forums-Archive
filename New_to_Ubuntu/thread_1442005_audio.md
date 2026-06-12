---
title: "audio"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by tooatw on 2010-03-29
the audio gives me lots of trouble 
on a laptop no audio works unless i remove pulseaudio but then audio from videos is not there, 
on my pc as well, i can only have on app that uses the audio opened at a time

will this ever get better?

p.s. its ubuntu 9.10 and yes i am a newcomer to ubuntu

---

### Post by readycarpenter on 2010-03-29
sound has always been an issue for me, I've learned to not install anything extra, as far as that goes, often loose sound after upgrade, but it could be something as simple as the pcm volume is down.

---

### Post by johnfrith on 2010-03-29
Have you considered the simodemd conflict? 

See:
[http://drowninginbugs.blogspot.com/2...io-in-910.html]("http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html")
&
[http://ubuntuforums.org/showthread.php?t=1441369](http://ubuntuforums.org/showthread.php?t=1441369)

John

---

### Post by agnes on 2010-03-29
> i can only have on app that uses the audio opened at a time

Have you considered setting the output audio device, for the app(s) that run together, to "ALSA" ?
(instead of e.g. set one to use ALSA, and the other Pulseaudio)
Somebody [here]("http://ubuntuforums.org/showthread.php?t=820305") had that problem when trying to use PulseAudio and Alsa simultaneously.

---

### Post by tooatw on 2010-03-30
> **agnes said:**
> Have you considered setting the output audio device, for the app(s) that run together, to "ALSA" ?
(instead of e.g. set one to use ALSA, and the other Pulseaudio)
Somebody [here]("http://ubuntuforums.org/showthread.php?t=820305") had that problem when trying to use PulseAudio and Alsa simultaneously.

i would rather not use pulseaudio at all, but if i remove it my multimedia keys don't work anymore so i have to open the gnome-alsamixer everytime i volume up or down
is there a fix to that?

---

### Post by NightwishFan on 2010-03-30
I do not know about the function keys, however if you try pulseaudio, sometimes you need to check volume levels manually using Alsamixer on the terminal.
```
alsamixer -c0
```

---

### Post by tooatw on 2010-03-30
> **NightwishFan said:**
> I do not know about the function keys, however if you try pulseaudio, sometimes you need to check volume levels manually using Alsamixer on the terminal.
```
alsamixer -c0
```
i use gnome-alsamixer to set volumes
still how can i make alsa take over the sound completely? 
as i said if i remove pulseaudio on a laptop the movie audio wont work anymore

---

### Post by NightwishFan on 2010-03-30
My point was (right or wrong) pulseaudio is not intended to be removed. You will have to search for a tutorial on how to do so. If I come across one I will link it to you.

---

### Post by tooatw on 2010-03-30
> **NightwishFan said:**
> My point was (right or wrong) pulseaudio is not intended to be removed. You will have to search for a tutorial on how to do so. If I come across one I will link it to you.
but can i move all audio tasks to something else other than pulseaudio then?

---

### Post by NightwishFan on 2010-03-30
The Ubuntu wiki says:
> If you decide you no longer like PulseAudio and would like to disable it: Remove the added lines to /etc/asound.conf If /etc/asound.conf did not exist when you installed PulseAudio, you may remove /etc/asound.conf entirely.

After this, you may remove all of the installed PulseAudio packages.

To disable pulseaudio in hardy you need to select alsa for for all options in /system/preferences/sound

 I believe this is depricated though because the /system/preferences/sound has changed.

---

