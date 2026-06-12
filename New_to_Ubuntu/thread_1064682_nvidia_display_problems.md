---
title: "nvidia display problems"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by freesitebuilder on 2009-02-09
I've got an Nvidia GeForce4 MMX440, and I'm running 8.10. I recently updated the driver so I could use compiz again (Nvidia didn't release a driver for use on 8.10 until recently).

Had a problem with Fx3, where the window border vanished and it started full-screen. I fixed that using another post on this forum, but now the problem is getting worse.

I had an idiot moment and decided to try cairo-dock, after a couple of days the display problems started again, but now compiz settings have vanished, window borders are gone on all progs, I get white blocks instead of some dialogue boxes (eg when it asks for password on Synaptic) and worst of all my terminal is a white blank. I've removed cairo, rebooted, but no change. I can't change quite a few settings on compiz, for example I can only use the wall and not the cube, and my icons in the notification area keep moving around whenever I restart.

I have the nvidia-settings installed, but even if I change the resolution it goes back to 1280x768 when I restart - I've saved to xconfig by running nvidia-settings with sudo, but they still change back on restarts.

I'm sure this must be a driver problem, but as it seems to go away sometimes I'm confused, so TIA for any help.

Turning off effects seems to work, just infuriating that it was OK for a couple of weeks!

---

### Post by dburnett77 on 2009-02-09
This is an older card, and it sounds like artifacts; which in Windows tend to be blurs.  With Xorg, they tend to catagorize to minimize them.

I'd suggest replacement.  Search for diagnostics packages, and test it.
Unfortunately, nothing lasts for ever.

---

