---
title: "minimize and maximize and close not visible in the window"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by dagarshali on 2010-05-01
Hi,
I just upgraded to 10,04 from 9.10 64 bit version. I have nvidia geforce 110M card installed on my laptop. After I upgraded it, any window doesnt' have the minimize, maximize and close option. If i go to system -> Preferences -> appearance and select either normal or extra desktop effects, only then i see minimize, maximize and close on the window.
After i did that, i rebooted it and the same size repeats until i manually change the desktop settings.

Any help?

Regards and thanks a bunch in advance..

Vishwa

---

### Post by baruch60610 on 2010-05-01
It isn't clear whether your maximize buttons are hidden by the window being too big, or whether they're simply not there at all.

If they're not there at all, I suggest you check to see whether you have a window manager going.  I don't know the name of the window manager.  KDE and Gnome use different ones.  Whichever environment you're using, find out what the proper window manager is.  Then at the command line, type:

ps aux | grep name-of-window-manager

If it comes up blank, then the window manager isn't running.  Entering its name would start it; I don't know how to convince the system to run it when you log on.  That may very well exist in the "Settings" menu option.

Sorry I can't be more helpful, but I hope this at least points you in the right direction.

---

### Post by david20063 on 2010-05-02
I was having the same problem when I was testing Lucid. My window manager is Metacity not sure what yours is. Typing it in the terminal will start it and to get it to start on start up i went to System>Preferences>Startup Applications and made and entry for metacity and it fixed it, turns out it was a bug and it was later fixed so I no longer needed to use a work around so you might wanna try reporting a bug as well.

---

