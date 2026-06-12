---
title: "Problem with video after update"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by pfeifferock on 2009-11-17
I am just updated my acer aspire 4530 to Karmic Koala and i when i play videos in VLC or in Movie Player it plays them in what i think must be inverted colors. and i can't play youtube videos in youtube but i can play them inbeded in other sites. any ideas?
-MAtt

---

### Post by brij on 2009-11-18
it happened to me once i just changed the video output and it worked well. change it under preferences and try X11 video output

---

### Post by pfeifferock on 2009-11-18
i found this in VLC and got it worked out but i can't find output in movie player.

Any ideas on the youtube problem?

---

### Post by 3rdalbum on 2009-11-18
Totem Movie Player uses the same settings as Gstreamer. The Gstreamer settings are stored in gconf-editor.

If your laptop has Nvidia graphics, try upgrading the driver as well. This is an issue that Nvidia has always kept running into.

---

### Post by pfeifferock on 2009-11-20
I am an extreme novice and i am gunna need a little more help figuring out where the gconf-editor is. my graphics card is navidia and it says that it has the latest update version 185. 
Any ideas on youtube/ most other streamed video not working?
-Matt

---

### Post by lotharmat on 2009-11-20
to get into gconf-editor

open a terminal (applications-->accessories-->terminal)
and type ```
gksudo gconf-editor
```
You will be asked for your password. 

iirc gStreamer settings are found in the 'system' folder

Have fun

---

