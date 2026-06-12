---
title: "Logitech Quickcam Pro 9000 really low framerate. . . ?"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-12-25
Hi!

I just got the Logitech Pro 9000, and while using luvcview, the frame rate is really slow (~5 FPS) .  No other application will even recognize the webcam.  Cheese, Camorama, Ekiga, Skype, all no luck.  I can adjust the microphone's preferences, but Audacity won't record from it.  I am using Ubuntu 8.10 32 bit.  Any ideas?

Thanks!

Happy Holidays!

---

### Post by pi.boy.travis on 2008-12-25
OK, a restart got Cheese working, but the frame rate is still really slow.

Also, Cheese crashes if I try to adjust the resolution.

Anything I can do?  Different drivers perhaps?

Thanks in a advance!

---

### Post by pi.boy.travis on 2008-12-25
OK, this is very strange.  luvcview will no longer work with the webcam, only cheese.  I have tried different ports on different machines, with no avail.  Any solution to this problem?

Thanks!

---

### Post by pi.boy.travis on 2008-12-25
Another reboot, and now nothing works.  The red activity indicator won't even come on.  The Pro 9000 is listed as compatible here: [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

What is going on?

---

### Post by dolorose on 2009-01-02
> **pi.boy.travis said:**
> Another reboot, and now nothing works.  The red activity indicator won't even come on.  The Pro 9000 is listed as compatible here: [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

What is going on?

Having a similar problem but not as bad. Quickcam pro 9000 works with skype and luvcview but not with anything else. Trying to get cheese to work at the moment.

---

### Post by pi.boy.travis on 2009-01-02
OK, I am having very good results with guvcview, because it allows me to adjust the exposure time.  I suspect the poor performance is due to my CF bulbs. . .  Earlier issues were caused by plugging the camera into an already packed USB hub.

Hope this helps. . .

---

### Post by DinoPower on 2009-01-11
I"m having the same issues with a logitech 9000 pro on a fresh build of 8.10.  I was able to load the updated kernel drivers per someone else's post on this forum, and now it works in skype, but not cheese.  

The frame rate though according to luvcview is very low, like 5fps as you mentioned.  the video looks choppy and not like it should for the cost of this camera.  Makes me a bit mad that the compatibility list shows this model to work "out of the box".  I would assume that if that list shows it works, someone is doing some testing and could back it up....guess not... oh well, I'll get over it. 

So here is the Q -what is the best way to control the settings on my camera?  I'd like to be able to mess around with resolution or other driver settings to see if I can get the frame rate up.  Has anyone else found a way to get the pro 9000 to work better than 5fps?

---

### Post by marfok on 2009-01-16
Hi,

to get the framerate up, you have to download and install the new version of luvcview.
You can find it here:
[http://www.quickcamteam.net/software/linux/v4l2-software/luvcview/](http://www.quickcamteam.net/software/linux/v4l2-software/luvcview/)

After you have installed luvcview you can turn off the auto exposure and increase it manually to e.g. 150 this should be 15 fps.

---

### Post by bear24rw on 2009-07-14
> **marfok said:**
> turn off the auto exposure

THANK YOU! Also you can use guvcview to adjust parameters my fps went from 5 to 30 by turning off auto exposure

---

