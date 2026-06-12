---
title: "Problem viewing remote webcam"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by exup1000 on 2010-02-01
Hi,

I have a wireless webcam for security monitoring, now that I have switched to Ubuntu I would like to get it working on the new O/S.

The webcam is accessed ok from a windows machine (running in Virtualbox), all I need to do is type in its address, IE will then prompt for user name to log in and the live feed is shown. IE does require some active X plugin called vivotek to play the mpeg feed.

Problem with firefox on Ubuntu is that I can log in and get to most of the controls but it does not show the live feed window, not even an X.

I have installed zone alarm and I can connect (I think) but its showing a black screen. But thats possibly because I dont know how to pass the user name and login.

Can anyone suggest what sort of plug-in or viewer I would need in Ubuntu to see the feed.

Regards

---

### Post by ukripper on 2010-02-01
I use zoneminder for such tasks. 

you can try this tutorial [http://www.linuxscrew.com/2007/11/05/howto-home-video-security-with-zoneminder-and-ubuntu/](http://www.linuxscrew.com/2007/11/05/howto-home-video-security-with-zoneminder-and-ubuntu/)

---

### Post by vnpifhf on 2010-02-01
i would recommend wine
 
i have one of those and i just go into the windows partition , edit the wine a bit and hey presto

---

### Post by t0p on 2010-02-01
The black screen makes me think it's a codec/plugin problem.  Try installing the Restricted Extras package:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by exup1000 on 2010-02-01
Thanks t0p I think you are right in that its a codec or plugin for firefox, but I already have installed the extras. Re run it just to be safe but no changes I am afraid.

Also thanks ukripper, already followed the tutorial and everything works but still a blank black screen. The tutorial does not cover how to pass a password into monitor. Their FAQ site states that I need to perform the following, but for some reason its not allowing me to enter these values.

[INDENT]Remote Host/Port/Path – Use these fields to enter the full URL of the camera. Basically if your camera is at [http://camserver.home.net:8192/cameras/camera1.jpg](http://camserver.home.net:8192/cameras/camera1.jpg) then these fields will be camserver.home.net, 8192 and /cameras/camera1.jopg respectively. Leave the port at 80 if there is no special port required. If you require authentication to access your camera then add this onto the host name in the form <username>:<password>@<hostname>.com. This will usually be 24 bit colour even if the image looks black and white.[/INDENT]

As for WINE, no need as I am running virutal box so in theory its emulating but I would prefer to try and get this running natively in Ubuntu.

Any one have any other ideas?

---

