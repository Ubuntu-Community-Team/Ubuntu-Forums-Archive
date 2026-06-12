---
title: "Skype - Mic not recognised"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by sammya on 2011-06-06
Hey guys. Have been at this for a while and cannot seem to find a fix that has worked so far.

I am using Ubuntu 11.04 and have Skype 2.2 Beta. The video is recognised but microphone isn't.

In Sound Devices (Skype) the Microphone, Speakers and Ringing options are all under "PulseAudio server (local)" and have no other options in the drop down menu.

I searched for the PulseAudio app and installed it, but still nothing.

My mic is working because I have tested it with the default Sound Recorder app from 11.04.

I am a complete noob and very lost, please help me.

Sam

---

### Post by KL_72_TR on 2011-06-06
See if this can help you: [https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting)

---

### Post by luckyelderberry on 2011-07-17
Hello, I'm another complete newby. 

I couldn't get my internal mic to work with skype either, but after lots of trying found that it was the Gnome Alsa Mixer app that did the job (not the other Alsa mixer I came across).

Once you've installed this app, go to the right hand capture slider switches and make sure the small horizontal ones at the bottom are all the way up to the right.

good luck

---

