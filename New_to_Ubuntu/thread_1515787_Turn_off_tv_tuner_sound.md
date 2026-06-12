---
title: "Turn off tv tuner sound??"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by fresnofred on 2010-06-22
I had a hard time getting my conexant based tv tuner's sound to work but finally succeeded by modifying the /etc/modprobe.d/options file with something i saw on an ubuntu forum but i neglected to bookmark the page. The sound now works but when I shut down tvtuner the sound stays.  I tried typing TOP in a terminal and saw 2 instances of pulse audio playing but i couldn't kill them.  i guess i modified my root file when i "fixed" the "no sound" option.  I wonder if there is an easy way to fix this?  Couldn't do it in Sound options by muting input or output.

---

### Post by fresnofred on 2010-06-22
partially fixed the no turn off sound in tv tuner.  downloaded "gnome alsamixer" from synaptic, made a desktop icon for easy access.  then muted cd function.  apparently the sound card only works when plugged into a cd connection on the motherboard and will continue to sound if cd is not muted. will try next to see if tv tuner works without connecting to mb but think i tried this before and it did not work.

---

