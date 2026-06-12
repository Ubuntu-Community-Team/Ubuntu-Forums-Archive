---
title: "Fuzzy sound issue"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by 801TomAK on 2010-03-19
now ima try to explain this as best as i can to help find a solution ok so heres the deal when i first start up my computer the sound works just fine now matter how loud anything is then like after a lil bit every thing gets really messed up like any kind of sound at all is just so fuzzy and distorted and iv tried turning down several sound things i could find thinking maybe thats the issue but its not no matter how low i turn it its still really fuzzy and messed up and i thing the problem might have started either when i installed wine or wow any ideas of what i might need to fix are add?? o and im running Ubuntu karmic

---

### Post by I8NY on 2010-03-19
Static sound should be only in apps and games not for ubuntu sounds.  Now the current audio driver "pulse audio" caused static in some apps and switching to ALSA fixed that.  You can get it by running, ```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get install alsa-base linux-sound-base alsa-utils
sudo apt-get install gnome-alsamixer
``` it should work now. ;)

---

### Post by 801TomAK on 2010-03-20
i think that fixed it ima keep this open for a lil bit longer just in case but no problems at all yet

---

### Post by I8NY on 2010-03-20
Just to let you know that the little speaker icon by the clock will no longer work but a different sound mixer is in Applications>Sound & Video>GNOME ALSA Mixer to change volume and set up a mic.

---

