---
title: "gnome-display-properties and login window problems"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by caravel on 2009-04-29
I'm using 9.04 32bit and have the fglrx version that is enabled with the hardware drivers applet running.  I have a few games installed and working, and compiz (now disabled) seems to be running ok.

I was trying to change screen resolution for no apparent reason and when I tried to start up gnome-display-properties it lagged horribly and only the outline of the window was visible.  I then decided to disable compiz, which made no difference.  I managed to kill the process and rebooted...

Now my login window is messed up.  The resolution and proportion is wrong and the login box itself is in the bottom right hand corner of the screen.  I can still log in, but I cannot access any of the options at the bottom now.

I've added the virtual resolution to xorg.conf, though I didn't need this before...

```
Virtual     1024 768
```

But this makes no difference whatsoever either (I'll post up xorg.conf later, as I'm at work now).

Going back into gnome-display-properties now yields the same results.  I can no longer access it, just the window outline and the cursor changes to the "working" cursor, with the whole system lagging and unusable.

I next decided to try purging fglrx and restoring xorg.conf.  This fixed the problem with gnome-display-properties and the login window.  Reinstalling fglrx again (and I mean redownloading it through hardware drivers because I removed the whole thing), brings me back to the same situation with gnome-display-properties not working and the login window messed up.

I've also tried ATI catalyst control center and I find that I usually can't change resolutions in there in 9.04, though I could in 8.10.  I can select a resolution and the prompt appears asking if it's ok, but it stays the same until I reboot.  My desktop resolution is fine though as it was before, the problem is the login screen resolution and gnome-display-properties.

Any help much appreciated.

Regards

Caravel

---

