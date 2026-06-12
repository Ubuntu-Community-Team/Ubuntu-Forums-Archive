---
title: "TX2500 ATI video drivers Vs Compiz"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by DrakeGis on 2009-01-14
Hi I have a HP TX2500 (ATI Radeon HD 3200). So far, a lot of progress in making work all the hard. However I have a really weird behavior with the video settings.

if Compiz is activated, when playing a video (no flash) the area where the video is being reproduced "flashed" showing the content behind it... this happens with totem, mplayer, Miro, etc. I have similar problems with Cheese, Camorama (doesn't work), Ekiga [which reproduce on screen what the webcam captures]).

if Compiz is deactivated the video reproduction works OK. Ekiga and Skipe (2.0.0.72-oss), capture the video OK. Cheese in both cases works only with the 160x120 resolution. Camorama still doesn't work.

I have the ATI drivers installed.

Any ideas ? A friend of mine support the idea that is a Compiz problem related with the overlay methods.

---

### Post by adamsu on 2009-01-18
I have experienced the same problem. If you are using the radeon driver (the non-proprietary driver), there is no 3d acceleration, but there is also no video problem. Also, I can only get screen rotation scripts to work if I am using the radeon driver. However, the radeon driver will not recognize a connection to a projector or external monitor, only the fglrx driver will. (I'm a teacher, so I use a projector daily in my classes.) 

The hack I use is to install the compiz icon, and switch the window manager to metacity when I want to play a video. This stops compositing the screen, so you won't get the flashing video. It isn't very convenient, but it works. If anyone knows a better way to fix this issue, please share with everyone!

---

### Post by mbzn on 2009-01-18
Hi

This seems to be a common problem with compiz
I installed compiz-switch which made it very easy to switch between metacity and compiz.

[http://linux.softpedia.com/get/Utilities/Compiz-Switch-37441.shtml](http://linux.softpedia.com/get/Utilities/Compiz-Switch-37441.shtml)

Hope this helps

---

