---
title: "Problem in sound drivers"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by SandyM on 2008-12-26
I am using Ubuntu 8.10 and it was working fine but from sometime I am facing some problems with my sound drivers (I am presuming that they are called drivers in Ubuntu)

Whenever, I try to play music, I receive a message displayed on upper left hand sign of my screen below SOUND icon and it is like this

[B][I]The audio playback device HDA Intel (STAC92xx Analog) does not work
Falling back to default.[/I][/B]

Although sound is coming and is fine but still there seem to be something wrong with the quality when compared to before.Moreover the message is quite annoying as it always appear when I Play the music.

PLEASE HELP ME and resolve the problem.

---

### Post by linux_tech on 2008-12-26
The audio playback device HDA Intel (STAC92xx Analog) does not work indicates, your hardware may not being detected properly by alsa
1st check output of 
```
at /proc/asound/card0/codec#* | grep Codec
aplay -l
```

```
 gksudo gedit /etc/modprobe.d/alsa-base

``` (to edit file)

add something like
options snd-hda-intel model=(depends on pc)

check this thread for full details-
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

