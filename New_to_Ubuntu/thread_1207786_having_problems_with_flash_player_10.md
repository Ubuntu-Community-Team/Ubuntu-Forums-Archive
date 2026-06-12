---
title: "having problems with flash player 10?"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by VVackDavid on 2009-07-08
i keep installing and uninstalling and reinstalling it but no matter how many times I do firefox doesnt seem to enable it because when i try to play a video it says i don't have the latest version of flash player.
might it have something to do with shockwave player?
i don't know...please help

(not a youtube video)

---

### Post by Ratscallion on 2009-07-08
When playing a video in YouTube no shockwave is used, so it can't be that if that is where you're playing the video... You may want to dive into add/remove, search for flash and install the Adobe Flash plugin 10... then log out, back in, start up firefox and all should be fine. I recommend leaving the Flashblock alone, it gets annoying, and can sometimes cause the flash to not work.

---

### Post by philinux on 2009-07-08
> **VVackDavid said:**
> i keep installing and uninstalling and reinstalling it but no matter how many times I do firefox doesnt seem to enable it because when i try to play a video it says i don't have the latest version of flash player.
might it have something to do with shockwave player?
i don't know...please help

(not a youtube video)

In a terminal execute the following two commands.

```
sudo updatedb

locate libflashplayer.so
```

The first one may take a bit to run with no output. It updates the database used by locate.

---

### Post by ajgreeny on 2009-07-08
Also check that you do not have installed swfdec or any libs for that, and gnash, as they may well interfere with adobe flash player.

---

