---
title: "mplayer became EXTREMELY slow!"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by kajman on 2009-02-09
My mplayer became extremely slow recently! It now takes about 10-15s after double-clicking on a movie file for it to load, and then another 10s (when it just shows white, blank screen) of waiting before the movie starts playing. What may be causing that?
Also CPU load is very low (4-5%) when it loads, so why do I have to wait so long? I just don't understand. 
Can it be somehow connected with changing every sound related option in my system to ALSA, which I did some time ago? But my audio settings in mplayer are also set to ALSA so I think there should be no conflict.
Any suggestions?

EDIT: I checked now, that when I have loaded a movie and paused it (which I did to make this post) and pressed start - I had to wait about 30s for the movie to play again. But when I press "pause" instead it plays it right away.

---

### Post by darkxman on 2009-02-11
Try 
> In MPlayer>Preferences>Misc Disable "Stop XScreenSaver"

That's suppose to stop the screensaver to show while you are watching a movie but if you're suffering from this delays at startup it doesn't seem to be working since MPlayer can't find it:

Quote:
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled 

---

### Post by kajman on 2009-02-16
Thanks, it helped a lot!

I hope my screen won't go off when I watch movies though. I'll check that later, thanks again!

---

### Post by EmilianoFraga on 2009-05-24
My Ubuntu is 8.04 and I had the same issue.

The above hint worked fine.

THANKS.

---

### Post by kajman on 2009-05-25
When I wrote this post I've also used Ubuntu 8.04 :)

---

