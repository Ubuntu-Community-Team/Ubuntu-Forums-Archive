---
title: "How to shut down?"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by rezabrya on 2009-11-26
I recently installed Xubuntu 9.10 on my Eee PC.  I have had Ubuntu NBR, Ubuntu 9.04, Xubuntu 9.04, and Xubuntu 9.10 on here.  Every other distro before this has had a shutdown button in the menu but Xubuntu 9.10 does not.  I click the logout button on the taskbar but instead of asking me what to do, it logs me out of my account which takes a lot of extra time.  How do I make it shutdown without logging out?

---

### Post by ceramicm on 2009-11-26
I don't know a graphical solution, but you should be able to open a terminal and use [FONT="Courier New"]sudo halt[/FONT] to shutdown.

You could possibly create a launcher with this command, but I'm not sure exactly how to do this in xfce.

---

### Post by winotree on 2009-11-26
In menu go to Settings | Xfce4 Settings Manager | Power Manager | General | When power button is pressed

There are five choices including Nothing, Shutdown and Ask.  There's way more information in this settings manager, too.

---

### Post by zainka on 2009-11-27
Yes, and no, cause there is also another setting that tweaks you, or did to me. I had by some reason the "prompt on logout" checkbox cleared in menu Applications | Settings | Xfce4 Settings Manager | **session and startup ** in the general tab. This will force a logout in stead of asking for what to do when clicking the exit button in the menue. I think this will solve your problems.

---

