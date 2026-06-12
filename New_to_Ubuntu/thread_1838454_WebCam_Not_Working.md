---
title: "WebCam Not Working"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by Intzi1992 on 2011-09-03
I Want to use webcam for skype .. and i go to skype settings and video divices and make the video test .. the camera work's perfect but when i am talking with someone camera is not working.. its showing that is loading but nothing happents..
And Finaly i read a forum that was say about all the webcam's and it was saying that about mine..

 Logitech [QuickCam]("https://wiki.ubuntu.com/QuickCam") PTZ 
    7.10 
    046d:08b5 
   PWC 
    Camera is recognized but 'Test Camera' shows  screen with vertical colored bars dancing all over the place.  Nothing  recognizable.  Camera works fine in Ekiga and Camorama 

So this mean's that it cant work?

---

### Post by no2498 on 2011-09-04
open a terminal copy and paste

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

click enter
thats for 32 bit
64 bit is something else like install libv4l/32bit then

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

