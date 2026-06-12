---
title: "audio not working"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by siddhuc on 2010-06-01
hi,
I am using compaq presario f700..i installed ubuntu lucid lynx and found that audio is not working.. i can find an audio icon at the task bar, but on selecting sound preference i am getting- No volume control GStreamer plugins and/or devices found..
Also, the mute all option is diabled.. how can i get the audio to work ?

---

### Post by siddhuc on 2010-06-03
when i run 
aplay -l
in terminal,it is giving no sound cards found.

---

### Post by forestG on 2010-06-03
Try downloading the pulseAudio packages. Maybe they will do the work.

Also try this:

From the top menus go to:
System->preferences->sound.

There check at the hadware tab to see if there is any hardware detected. If any try GStreamer,PulseAudio and anything else.

I had a similar problem with ubuntu 9.10 and the problem was the GStreamer. Try going to Synaptic Manager (System->Administration->Synaptic Package Manager) and try removing any Gstreamer drivers and install PulseAudio or something else. 

I am a new user in Linux too. So to be truly honest there is little chance that my suggestions will work.

---

