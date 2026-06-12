---
title: "rocketfish 7.1 pci sound card????"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by JustinHicks on 2010-03-11
alright guys i have a 7.1 channel surround system that i'm trying to set up ... so i dumped my onboard audio (cuz it's not 7.1) and went and bought a 7.1 el cheap-o for 50 bucks down at best buy... but i can not get it to work on ubuntu! i have the driver cd... but i'm doubting that helps with linux any ideas on how to get this up and running on my fresh ubuntu system??? thanks in advance and just so you all know i'm very new to this so i'm sorry if i'm making something harder then it is...

---

### Post by aceracer24 on 2010-03-12
> **JustinHicks said:**
> alright guys i have a 7.1 channel surround system that i'm trying to set up ... so i dumped my onboard audio (cuz it's not 7.1) and went and bought a 7.1 el cheap-o for 50 bucks down at best buy... but i can not get it to work on ubuntu! i have the driver cd... but i'm doubting that helps with linux any ideas on how to get this up and running on my fresh ubuntu system??? thanks in advance and just so you all know i'm very new to this so i'm sorry if i'm making something harder then it is...

If it's the one I think it is, it should be using the x-fi audio chip. I would think it would be detected just like the normal X-fi cards do. Did you try going into the audio menu and select that specific card to be used for playback? Beyond that, I won't be of much help.

---

### Post by cascade9 on 2010-03-12
Actually, despite the name, its not a 'real' X-fi. Its actually based on the audigy series cards. 

It should be at least partially supported by the current alsa drivers. 

There is a thread about how to get it going for the older versions of ubuntu here- 

[http://ubuntuforums.org/showthread.php?t=534318](http://ubuntuforums.org/showthread.php?t=534318)

If you're still having problems in a day or so I'll try to figure out whats wrong...but I'm guessing you might just need to reinstall alsa. I think  :|

*Edit- #$%$#^! creative.

---

### Post by JustinHicks on 2010-03-12
alrighty... this is what i did i installed alsa-driver-1.0.22.1.tar.bz2 as per [http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html]("http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html") after competing this it said in the terminal Warning Audio driver muted by default change it with a "mixer" you can use an alsa mixer or an oss mixer to do this. Well there is the problem maybe i do not have a oss or alsa mixer at least to my knowledge if so i cant find it... how would i get a mixer?

---

