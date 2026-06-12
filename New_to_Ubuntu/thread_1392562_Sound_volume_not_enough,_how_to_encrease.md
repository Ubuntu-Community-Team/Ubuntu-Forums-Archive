---
title: "Sound volume not enough, how to encrease"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by Ubunser on 2010-01-28
Using laptop and maximum sound is ridiculously low I mean compared to that in windows it's like only half possible.

---

### Post by Chilli Bob on 2010-01-28
New install?  Try right-clicking the volume control icon and select "Open volume control".  Turn up the master volume slider and see if that helps.  It is often set quite low by default.

---

### Post by Ubunser on 2010-01-28
> **Chilli Bob said:**
> New install?  Try right-clicking the volume control icon and select "Open volume control".  Turn up the master volume slider and see if that helps.  It is often set quite low by default.

No I'm using 9.04 and I know that simple stuff. I mean Ubuntu sound sucks! not my computer configuration. But thanks anyway.

---

### Post by philinux on 2010-01-28
> **Ubunser said:**
> No I'm using 9.04 and I know that simple stuff. I mean Ubuntu sound sucks! not my computer configuration. But thanks anyway.

Your first post relates to volume level not quality. Which is it?

---

### Post by ajgreeny on 2010-01-28
I have only just written this in another post; give it a try if you have not already done so.
In a terminal run ```
alsamixer 
```
 if you have not already done so, and check if any of the sliders that shows are muted or too low. Use cursor keys to move from slider to slider and raise up and down for their levels, "M" to mut/unmute and tab to move from Playback to Capture to All. Esc to exit. It often finds things you won't even know are there, and are perhaps, set far too low.

---

