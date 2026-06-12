---
title: "Sound quality very poor"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-12-27
I have an intel integrated sound card:

Card: HDA Intel
Chip: Conexant CX20551 (Waikiki)  

Recently I have noticed that the quality of my mp3's in rhythmbox is very poor compared to when I play them on my ipod. In fact everything (including movies played on SMPlayer) sounds very muffled and with too much bass (it does not seem very "crisp"). I think this has something to do with the PCM settings, but I have tried every conceivable level of volume (from extremely high to medium).

I recently wrote the following guide to remove pulse audio: [http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html](http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html)

It works well enough and the problems that I have with skype are gone. However, now I am begining to wonder whether removing pulse means that ALSA is giving problems.

Anyway I'm not sure what the problem is, except that all sound on my computer seems muffled.

Thanks for help!

---

### Post by 2hot6ft2 on 2008-12-27
Thought I would give a little more info. And replaced my first post by mistake so it will be below.

On my desktop this worked best. Running Hardy Ultimate 64 bit
Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)

On my laptop this is working great and the system wide eq. makes it rock. Running Intrepid 8.10 Ultimate 32 bit
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by 2hot6ft2 on 2008-12-27
First fixing pulse
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
maybe you can find something you missed here.

---

### Post by abhiroopb on 2008-12-27
Hey I followed the following: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

and basically sorted out my issues with pulse. Yet it still sounds a bit muffled and the bass seems to heavy. The crisp volume is lost.

Also with pulse I still have:

1. Master Volume
2. PCM
3. Pulse volume control

There are so many different ways of raising and lowering the volumes I'm a little confused.

What is the ideal setting for PCM? Should it be on full? What about the other pulse volume settings?

Managed to sort out skype.

---

### Post by abhiroopb on 2008-12-27
I followed the entire guide and now I have the following problems:

1. Randomnly pulseaudio will crash/quit with the following error:
```

Soft CPU time limit exhausted, terminating.
Segmentation fault

```

2. I tried to use the "System-Wide Equalizer Support" but I get the following error. Well actually now I can't reproduce that error because I keep getting the following (even after restarting):

W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: pid.c: Stale PID file, overwriting.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL equalized
Segmentation fault

---

### Post by linux_tech on 2008-12-27
pulseaudio can be stopped
```
gksudo killall pulseaudio
```

if you wish to restart it-
```
gksudo pulseaudio
```

pulseaudio alternative-
[http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

---

### Post by abhiroopb on 2008-12-27
Does that help with my sound quality problem?

---

### Post by linux_tech on 2008-12-27
You can try stopping pulseaudio to see that improves the sound.
If you havn't already installed these under Intrepid, installing these  will probably improve your sound


```

sudo apt-get install alsa-oss

sudo apt-get install libasound2

sudo apt-get install libasound2-plugins

```

---

### Post by abhiroopb on 2008-12-27
what do these packages do?

I have tried disabling pulse and that does not work very well so I have decided to try using it.

---

