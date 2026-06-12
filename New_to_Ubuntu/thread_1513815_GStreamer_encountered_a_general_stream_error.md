---
title: "GStreamer encountered a general stream error"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by noworldorder on 2010-06-20
I am using Totem Movie Player 2.30.2 and it has been working fine but suddenly it can't play anything and I get this error:


"GStreamer encountered a general stream error"

I tried playing the same movie with VLC Media Player and it says:

"The AVI file is broken. Seeking will not work correctly. Do you want to fix it?"

The problem is not the file - none of my files play in either program.

Help please..  
thanks

---

### Post by bigseb on 2010-09-05
I get the same error... any fix for this. 

I am using (or would like to use) Movie Player to watch DVD's.

---

### Post by no2498 on 2010-09-05
ok this works for me it comes from the program cheese

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


best i can say hope it helps you 2

---

### Post by bigseb on 2010-09-09
> **no2498 said:**
> ok this works for me it comes from the program cheese

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


best i can say hope it helps you 2
What you wrote is way over my head... Did try "gstreamer-properties" in terminal though and got this (see attachment):

[ATTACH]168927[/ATTACH]

---

### Post by no2498 on 2010-09-16
reread the plugin yours is set to auto

---

