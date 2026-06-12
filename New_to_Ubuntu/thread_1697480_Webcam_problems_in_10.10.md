---
title: "Webcam problems in 10.10"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by Ryan-165 on 2011-02-28
Hey, im using a CompaqPresario CQ60 and the built in webcam has suddenly stopped working. Whenever I try it on Cheese or anything else, i jsut get lots of lines :S Ive tried searching for drivers and installing some updates, but no joy. Any chance i could get it to work again?

---

### Post by no2498 on 2011-03-01
cheese has a nice help file in the FAQ's

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.
    


use the bottom test button till you get the cam working

---

### Post by Ryan-165 on 2011-03-01
Cool, il give that a wee shot. Cheers! :)

---

### Post by Ryan-165 on 2011-03-01
Nah still didnt work. I tried everything in gstreamer properties, and i keep getting this error message: 

Video for Linux 2 (v4l2): Could not get buffers from device '/dev/video0'.

I navigated to that directory & dont see a file called video0. Could that be the problem?

---

### Post by no2498 on 2011-03-02
look in your package manager for xawtv and install it try the cam in it

---

