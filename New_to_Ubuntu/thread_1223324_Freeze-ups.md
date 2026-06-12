---
title: "Freeze-ups"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by MattTheRicker on 2009-07-26
Hey there. I am having some issues with freeze-ups. It doesn't happen very often - maybe once every two days or so. The computer will be on screen-saver (just one of the regular screen savers that came with Ubuntu), I bring it out of screen-saver, it runs fine for 2-4 minutes, then it randomly freezes in place and the computer will not accept input from the mouse or keyboard, and I have to do a hard restart. Again, this does not happen every time I come out of screen-saver, just every once in awhile.

Any ideas?

---

### Post by Ravernomina on 2009-07-26
it could be one of these things

1. you driver for your Video card might not be the best for ur computer... U might need to reinstall or check for updates.

2. If your on EXT4 filesystem this is slightly normal the filesystem is not that stable yet atm its still needs a few patches.

3. Your Xorg could be crashing or trying to awake after having the screen-saver up. try typing in terminal "TOP" and see if Xorg is still running after wake.

4. you might have a few disk errors trying running a disk check with Gparted or the terminal command (witch i do not know right now sorry).

All of the best
   Ravernomina

---

