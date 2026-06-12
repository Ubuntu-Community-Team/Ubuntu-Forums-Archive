---
title: "No sound in Flash videos (TRIED EVERY THREAD I CAN FIND!)"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by digdugdiggy on 2009-01-28
Im running Ubuntu 8.1, Firefox 3.0.5, using ALSA sound.

Suddenly, no audio plays from flash movies. (Still have sounds in movies/mp3 files)

I have search google, and tried every solution I can find, all the way back to page 5.

Can anyone suggest anything? I really enjoy youtube, but no sound is rough.

I tried reinstalling Flash player, no beans. I heard about editing a mozilla file to point to AOSS, but there is no config there. I tried to AOSS Firefox as well, no beans.

Any help? Thanks.

EDIT NOT SOLVED

---

### Post by kostkon on 2009-01-28
I would like to ask:
Do you have two soundcards (for example one PCI, one onboard)?

---

### Post by Crafty Kisses on 2009-01-28
You might find this link useful: [https://launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760](https://launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760).

---

### Post by kansasnoob on 2009-01-28
Run through all the appropriate steps here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by digdugdiggy on 2009-01-28
> **kostkon said:**
> I would like to ask:
Do you have two soundcards (for example one PCI, one onboard)?

Yes, I do actually. 
One is built in (Not sure I can check)
the PCI one is a Creative Soundblaster Audigy SE.

In case the info is needed: Im using 3 (1/8") small audio jacks to my 5.1 surround speakers. I have an also script that plays stereo to all speakers, but this functioned before with flash videos.

I will try the above posters ideas and check back.

---

### Post by digdugdiggy on 2009-01-29
> **kansasnoob said:**
> Run through all the appropriate steps here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)



THANKS! This solved my problem. Audio now works in Flash and through mp3's. 

Does editing the asound.rc (Steps told me to erase it) work the same with pulse audio? I had my 5.1 speakers set up to work with Stereo sound.

---

### Post by digdugdiggy on 2009-01-29
So I solved the problem, then proceeded to break it again.

After getting it to work I added
> pcm.!default {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.5 0.5
    ttable.1.5 0.5
    ttable.0.4 0.8
    ttable.1.4 0.8
}

To my asound.rc

and then I uncommented the line in /etc/pulse/daemon.conf "default-sample-channels" and changed the value from 2 to 6.

After this, and some messing with the mixing of my 5 speaker volume levels, youtube videos do not work again.

I tried to re-follow the steps listed that worked, but they do not fix the problem. I hear faint static during flash movies.

---

### Post by digdugdiggy on 2009-01-29
I figured out the solution.

I left clicked my PulseAudio applet tray icon > Default server > Checked "default"

Somehow, nothing was checked under that menu, but it solved youtube videos..

Strange.

---

