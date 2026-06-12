---
title: "No video in Totem Movie Player"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by user_linux on 2011-08-30
There is no video, only sound when I play a DVD on Totem movie player, but when I enlarge the screen, then I see video. How can I solve this problem?

---

### Post by kyletstrand on 2011-08-30
Try this:

Open a terminal and run
```
gconf-editor
```
Find system > 0.10 > default.
Click on videosink and change setting from autovideosink to ximagesink

Not sure if this will work for DVDs, but it works for other formats.

---

### Post by user_linux on 2011-08-30
Thanks a lot, not sure how this setting made a difference but it did, it even solved my mozilla totem plugin problem :)

 
> **kyletstrand said:**
> Try this:

Open a terminal and run
```
gconf-editor
```Find system > 0.10 > default.
Click on videosink and change setting from autovideosink to ximagesink

Not sure if this will work for DVDs, but it works for other formats.

---

### Post by kyletstrand on 2011-08-30
Glad it worked!

---

### Post by avroarrow on 2012-01-24
I have ubuntu 9.10 installed. I have installed all gstreamer programs. my music cd works ok. but when I put in a movie dvd nothing happens.

---

### Post by Norabunny on 2012-05-15
Brilliant! Thankyou, trawled ages for an answer that worked.

---

