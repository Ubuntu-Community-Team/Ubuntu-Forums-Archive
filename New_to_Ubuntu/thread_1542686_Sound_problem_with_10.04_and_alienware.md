---
title: "Sound problem with 10.04 and alienware"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by MAG1113 on 2010-07-30
Hey everyone, 

I've been using Ubuntu for a few months now, and every time i've installed or updated i've had to deal with this same problem. Despite searching, i couldn't find a fix this time after doing a fresh install. 

I'm using an Alienware M15X and am running Ubuntu 10.04. My issue is that, despite being able to get sound through the headphones, nothing comes through the speakers. I've checked my volume and have also downloaded Gnome-Alsa Mixer and PulseAudio, as i remember them having something to do with the fix the previous times i've had this issue. 

any help would be appreciated.

---

### Post by MAG1113 on 2010-07-31
Hey,

Another few answers and i found the fix, i figured i'd post it here in case anyone else needed it.

i found the answer here:

[http://swiss.ubuntuforums.org/showthread.php?p=8010875](http://swiss.ubuntuforums.org/showthread.php?p=8010875)

And the gist of it was to go into 

     /etc/modprobe.d/alsa-base.conf

and add this line to the bottom of it

     options snd-hda-intel model=3stack-6ch-dig

---

