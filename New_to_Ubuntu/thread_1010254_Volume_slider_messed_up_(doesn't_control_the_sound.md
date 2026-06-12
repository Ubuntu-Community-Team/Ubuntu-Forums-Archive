---
title: "Volume slider messed up (doesn't control the sound well)"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Adamantus on 2008-12-13
I have an HP dv5 with the volume touch sensitive buttons on the keyboard. They all work (mute, volume slider, etc.), but the volume slider doesn't control the sound too well. It's sort of hard to explain. I can only decrease the sound to about 3/4 maximum before the sound becomes nearly silent, and it increases extremely quickly to maximum. It seems to be operating only in that top fourth of the bar, so I'm either stuck at really loud or really soft. I have the same problem with the Gnome icon (where only the top fourth of the slider is audible.

And my sound options are set to HD ATI SB (Also Mixer): Master, SCM, Front

---

### Post by Adamantus on 2008-12-13
bump

---

### Post by jewblahsky on 2008-12-27
i'm having the same problem, same machine, intrepid 8.10. to illustrate, the dashes represent the volume slider, with the most dashes indicating the slider's top-most position. the percents are how loud the volume actually is at that slider level.

--------- 100% 
--------   50%
-------    25%
------      0%
-----       0%  
----        0%
---
--
-           0% 

any ideas?

---

### Post by Coder543 on 2008-12-27
Double click the volume control and make sure Master, PCM, Headphone, and Front are all maxed out. Then try the slider again. Also, in my experience the slider works more exponentially then it does linearly.

---

### Post by jewblahsky on 2008-12-27
that seemed to help a little, but volume is still at 0% when the slider is about at 50%. is this common? if so, it doesn't make much sense...

---

### Post by hai_long21 on 2009-01-05
hey, this is my first post on a ubuntu forum!!

I have the exact same problem... and I kind of found a solution... however... it will still mute when the slider is at around 50%

i found this on another forum:

in terminal type: gconf-editor

then open /apps/gnome_settings_daemon

by default there is a number 6.... so when the slider increments/decrements the volume by 6%.... i changed it to 1% so now I have a better control of my volume.
I found this helps a lot but I still find it annoying that it mutes at half

hope this helps!!!

---

### Post by jewblahsky on 2009-01-06
good find, hai. but i agree, having no sound at 50% volume is quite annoying.

---

### Post by theblackred on 2009-01-12
I don't understand how no one has a solution to this. I've been looking for two weeks and there are no posts about this problem that have been resolved.

---

### Post by Fass on 2009-01-12
Tried using alsamixer and seeing if all your outputs are at decent levels? I had similar problems until I upped the volume there.

```
alsamixer -D hw:0
```

---

### Post by theblackred on 2009-01-12
All the sliders are at their maximum levels, but the volume is still mute when the master volume is around 50%.
Also, that's what coder543 suggested already. 
Any other suggestions?

---

### Post by jewblahsky on 2009-01-15
I found that if I changed the control device from "HDA Intel (Alsa mixer)" to "IDT 92HD71BX (OSS Mixer)," the slider has full range volume control (although the volume becomes negligible at about 20% slider).

However, using headphones the slider control is even worse, zeroing the volume at about 75% of the slider.

---

### Post by theromanone on 2009-02-07
> **hai_long21 said:**
> hey, this is my first post on a ubuntu forum!!

I have the exact same problem... and I kind of found a solution... however... it will still mute when the slider is at around 50%

i found this on another forum:

in terminal type: gconf-editor

then open /apps/gnome_settings_daemon

by default there is a number 6.... so when the slider increments/decrements the volume by 6%.... i changed it to 1% so now I have a better control of my volume.
I found this helps a lot but I still find it annoying that it mutes at half

hope this helps!!!


holy... thank you so much. this works perfect.

---

