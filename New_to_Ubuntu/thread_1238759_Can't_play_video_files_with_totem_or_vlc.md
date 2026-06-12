---
title: "Can't play video files with totem or vlc"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by sean_Brown on 2009-08-12
Hey I have been trying to play .avi files and other formats through totem and vlc but it just shuts down when starting up.  I get this error message when running a file through vlc.
I have also install ubuntu-restricted-extras, and flash.  I am not running compiz.



[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

---

### Post by zeroseven0183 on 2009-08-12
Well, I'm not very good in interpreting codes like that but I think what it means is that your computer does not have enough resources to play video files.

Can you post here the hardware specs of your computer?

---

### Post by sean_Brown on 2009-08-13
Acer Aspire 3680.  Integrated Graphics.  Intel Celeron M.  1.5G RAM.

---

### Post by halitech on 2009-08-13
how much ram do you have and what are  your graphics set up like? ie. resolution and amount of video ram?

---

### Post by sean_Brown on 2009-08-13
1920*1200. 128mb

---

### Post by NightwishFan on 2009-08-13
I fixed problems with my intel card in totem by disabling Xvideo in gstreamer-properties.

Press alt+f2 and type:
```
gstreamer-properties
```
Under video settings change it from X11/Xv/shm to just X11.

For VLC:

Under preferences, go to video, and set it to use x11 video.

---

