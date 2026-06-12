---
title: "Trying to fix my sound (Hardy Heron)"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Lakeside5 on 2008-12-07
Going to take another try at this, I just let it go for a bit, as I tried before and it was a disaster don`t ask ;)  But I would like to have some sound on here,  After I installed Ubuntu Hardy Heron server edition, well I have no sound at all.  I do have a sound card listed (did a search in terminal) but a am confused how to proceed. I`ve read conflicting things when I google. thanks

---

### Post by kansasnoob on 2008-12-07
Start here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Once you know your sound card is recognized go here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

If you end up with working but very weak sound install gnome-alsamixer from synaptic and look for it in Sound & Video, then crank up the first three toggles and the last four (VIA) toggles.

---

### Post by Lakeside5 on 2008-12-07
Thanks very much kansasnoob, wish me luck.

---

### Post by Lakeside5 on 2008-12-07
I must be doing it wrong.  I started out entering this line, exactly like this, at the root: mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/  and then this one after it was finished: sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf,  and then step 3, and 4, and 5 (and then saw pulseaudio WAS listed in applications)  But when I tried `Open the PulseAudio Volume Control application` select volume control, and try to set volume meter playback and recording, I get `no default sink set`. If I try to launch it from the terminal, I see `segmentation fault. If I just click on `volume control` in the menu, I don`t see anything, something goes by so quick, I don`t see it. I look in `Manager` and see that default sink and default source are not set. so I check default source,  default sink, and default server and  and no network devices are found. What am I doing wrong please :(

---

