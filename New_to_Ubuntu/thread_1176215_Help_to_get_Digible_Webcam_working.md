---
title: "Help to get Digible Webcam working"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by mcci6 on 2009-06-02
I've just installed Ubuntu 8.10 on my laptop (currently dual booting with XP) to give it a try. 

I'm trying to get my (little known) Digible webcam to work with Ubuntu 8.10 but I'm having some difficulties and am not familiar enough with Ubuntu to tinker with it. 

So far I've tried testing it on Ekiga and it works to an extent - so when the webcam is facing me, I can see an image but the image is split so that the top quarter of the image is shown again at the bottom below a green static line i.e. the top of my head appears again at the bottom of the screen. The remaining three-quarter of the image above the green static line is clear, but the image below the green line alternates between a double-image and a zoomed-out pink and green double-image.

When I tried it with gstreamer-properties with settings on:
- Video - Default Output - Plugin: Autodetect
- Video - Default Input - Plugin: Video for Linux 2 (v4l2)
- Video - Default - Device: USB2.0_Camera
The test output shows multi-coloured boxes and a static box in the right bottom corner of the screen.
The test input crashes the application and terminal notes "Segmentation fault". Although one time I did manage to get the same faulty image as the one I got through Ekiga shown.

My main goal is to get it working in Skype - and so far when I test it in Skype, nothing shows. In Skype options under "select webcam" is USB2.0_Camera (/dev/video0).

I have no idea what all these means, so any help or direction to get the webcam working would be much appreciated. Thanks.

---

### Post by mcci6 on 2009-06-05
Here's some more information in case it helps with diagnosing the problem. I'm adding info that others with webcam problems have been asked to provide.

For: lsusb
Result:
Bus 005 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 093a:2700 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

For: luvcview
Result:
luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: YUYV (MJPG is not supported by device)
  Frame size:   640x480
  Frame rate:   30 fps

The webcam image that pops us shows the upper third only - the upper third image is nice and clear. The rest is green.

Anyone able to help with getting my webcam to work?

Thanks.

---

### Post by mcci6 on 2009-06-10
Hi again,

Can anyone offer any help or suggestion to solve my webcam problem?

Anyway, I've been doing more research online and I tried to check whether my webcam is UVC compliant using the info from [http://linux-uvc.berlios.de/faq/](http://linux-uvc.berlios.de/faq/). 

I think my webcam is UVC compliant based on the following result, but what does the last three lines mean? Can anyone help?

lsusb -d 093a:2700 -v | grep "14 Video"
      bFunctionClass         14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Thanks.

---

### Post by mcci6 on 2009-07-21
I've finally gotten my webcam to work in Ubuntu 8.10 (kernel 2.6.27-14-generic). I researched the internet extensively for similar problems and I finally selected a solution to try... and it worked!

I followed the solution below provided by Teamgeist in this forum thread: [http://ubuntuforums.org/showthread.php?t=987023](http://ubuntuforums.org/showthread.php?t=987023) (thanks, Teamgeist!)

I'm not exactly sure what did it - but I think the solution was to update the UVC drivers that came with Ubuntu 8.10.

-----------------

Copy this all at once into a Terminal and hit 'Enter'. Not line by line but all at once.

Code:

sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
wget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
sudo make install &&
sudo depmod -ae $(uname -r)

Restart your computer and cheese should work just fine.

---------------

Now my webcam is working with Ekiga, Cheese and also Skype. Yay!

Hope this helps someone else.

---

