---
title: "Logitech QuickCam for Notebooks doesn't work"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by ElTron on 2010-03-06
Hi

My Logitech, Inc. QuickCam for Notebooks doesn't work with Ubuntu 9.10. 

Any ideas??

Thanks

---

### Post by Djalmahal on 2010-03-06
Did you install "cheese" from synaptics?
You were a bit short in your description.
What's the actual model? Is it an external webcam?

---

### Post by ElTron on 2010-03-07
OK, you are right. That's given by lsusb:

us 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 046d:08dd Logitech, Inc. QuickCam for Notebooks
Bus 002 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The computer is an AMD64 with Ubuntu 6.10 for 64 bits.

What is cheese for?

I'm a newbie

---

### Post by patchwork on 2010-03-07
Cheese is a web cam software package (for taking pictures, videos, etc)  If it works, then we can try to narrow down the specific problem you are having.  You can install cheese by typing:

```
sudo apt-get install cheese
``` in the terminal, or by searching in the Ubuntu Software Center for cheese

---

### Post by switch10 on 2010-03-07
I have one.  I installed cheese, and it works fine...

---

### Post by inobe on 2010-03-07
> **ElTron said:**
> Hi

My Logitech, Inc. QuickCam for Notebooks doesn't work with Ubuntu 9.10. 

Any ideas??

Thanks

best bet is telling us what app you want to use, if it's skype' where did you get skype, also have you run the video and sound tests and selected the devices from skypes drop down menu's.

---

### Post by mchristian on 2010-04-23
I just installed the upgrade to Ubuntu 10.04 from 9.10 and my webcam now works perfectly with all applications without any modifications. I dont know what they did but it seems to me no longer an issue on my laptop.
Quick Cam for Notebooks  08dd
Compaq Presario V5000

---

### Post by no2498 on 2010-04-23
if it does not come on in cheese
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2

now try cheese
if it stops working at any time redo this

---

### Post by noob555 on 2010-04-26
Hi Everyone,

I have a Logitech Quickcam for Notebooks, ID 046d:08dd.
I'm running Karmic 32-bit, on an IBM X41 Thinkpad.

Until recently, the video on Skype worked if I opened Skype by using the following workaround, which is now well-known.

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

But a couple weeks ago it stopped working.  I don't know why.  Now I can't figure out any way to get my outgoing video to work in Skype.  The [SkypeWebcams-Wiki]("https://wiki.ubuntu.com/SkypeWebCams") does not indicate a workaround.

I appreciate any help that you can offer.  This forum is always the best!

---

