---
title: "Set Monitor as Default"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Uubnewb on 2009-06-18
How can I set the non-default monitor as the default one in Ubuntu 8.10?  The one monitor is an LCD connected with a DVI cable, the other is a CRT connected with an analog cable.

I want to set the LCD as my default monitor, but for some reason the CRT always end up as the default.  What I have done so far is go to System/Administration/NVIDIA X Server Settings; click on "X Server Display Configuration" in the left-hand panel; click on the LCD monitor in the right-hand panel; tick the "Make this the primary display for the X screen" box; click "Apply"; click "Save to X Configuration File."  I then get a message saying "Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'" and when I relog, my CRT is set as the default screen again.

Anyone know how to fix this?

---

### Post by The Cog on 2009-06-18
Just a wild guess (I can't try it now), but try System->Preferences->Display, and drag the screens round to change the order. Then log out/in again and see if that makes any difference.

---

