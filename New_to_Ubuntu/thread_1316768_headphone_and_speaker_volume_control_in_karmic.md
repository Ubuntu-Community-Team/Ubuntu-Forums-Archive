---
title: "headphone and speaker volume control in karmic"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by seamustry on 2009-11-06
i have a dell d610 laptop and installed 9.10. 

i can't get the volume of both headphones and speakers to go up and down together. i can only control the speaker volume using my volume buttons. i was able to change some settings in 9.04 to get this to work but it seems a lot of stuff has changed in this new release.

any ideas??

thanks.

---

### Post by seamustry on 2010-01-18
bump! :)

---

### Post by lev-unr on 2010-01-18
Have you tried fiddling with Alsa Mixer?

In the terminal just type alsamixer 

then you can manually adjust all the levels. It can be a pain if you are constantly adjusting them but its a one time fix. (this is what I did to get my internal mic towork)

---

### Post by -kg- on 2010-01-18
[LIST]
[/LIST]

Alternatively, you can install either "gnome-alsamixer" or "alsamixergui" from Synaptic.  You might try one, then the other, and see which works best for you.

That would beat launching the terminal every time you wanted to adjust volume levels.

---

