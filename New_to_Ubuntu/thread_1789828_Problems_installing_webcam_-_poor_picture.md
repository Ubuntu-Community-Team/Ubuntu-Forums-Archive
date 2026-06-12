---
title: "Problems installing webcam - poor picture"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by Jermuk on 2011-06-24
I am trying to install a cheap Tesco webcam on my Wubi-installed Ubuntu 10.04, and I'm running into difficulties. Cheese recognises the webcam and shows a picture, however the contrast is completely off - it appears very dark and the quality is terrible. Neither Camorama or guvcview work,  giving errors of "Unable to capture image" and "Can't set a valid video stream for guvcview" respectively.

The output from lsusb:
> Bus 005 Device 007: ID 093a:2468 Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye WebcamI tried Googling, and the most common suggestion of doing "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese" doesn't make any difference.

Thanks in advance from any help, please bear in mind I'm a complete beginner to Linux!

---

### Post by ubudog on 2011-06-24
Hi there!  Welcome to Linux/Ubuntu!  

Have you taken a look yet at the preferences in Cheese? 

While in Cheese:
Click on Edit>Preferences.

---

### Post by Jermuk on 2011-06-24
> **ubudog said:**
> Hi there!  Welcome to Linux/Ubuntu!  

Have you taken a look yet at the preferences in Cheese? 

While in Cheese:
Click on Edit>Preferences.

Cheers for the reply, that was the first thing I tried! Adjusting the sliders does nothing to improve the picture, and I would have thought that the fact that no other app I've tried has managed to even produce a picture would indicate a more complex problem!

I should also mention that the webcam works fine on Windows, so it's not a dodgy camera.

---

### Post by no2498 on 2011-06-25
install v4l2ucp
it comes up in ( system , preferences ) as video4linux control panel

you can set a few things in it
hope it helps you

---

### Post by Jermuk on 2011-06-25
> **no2498 said:**
> install v4l2ucp
it comes up in ( system , preferences ) as video4linux control panel

you can set a few things in it
hope it helps you

That does seem to be much better, thanks! Changing the exposure in particular improved the picture a lot. It's still nowhere near the quality it was on Windows but I guess I'll just live with it.

Thank you both for your help!

---

### Post by ubudog on 2011-06-25
Well, glad you got it kind of fixed.  :-) 

In the future, when buying webcams, I recommend Logitech or Creative, as those *normally* work right out of the box with Ubuntu.  You can find a detailed list here:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

---

