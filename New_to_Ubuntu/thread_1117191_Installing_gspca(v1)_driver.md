---
title: "Installing gspca(v1) driver"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by OllieGab on 2009-04-05
Tried to install the gspcav1 driver via the command line but got some error messages. Found a little install program using the synaptic package manager, called easygscpa, which started to install but seemed to freeze in the middle of it and I don't think the driver was ever installed.

Anyone know exactly how to install this driver? 

Ollie

---

### Post by spiderbatdad on 2009-04-05
[http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)
I dont think the one in the repos works, unless it has been fixed.

---

### Post by OllieGab on 2009-04-05
I get about half way through and then get this output:

ola@ola-desktop:~/cam/gspcav1-20071224$ sudo rmmod gspca
ERROR: Module gspca does not exist in /proc/modules
ola@ola-desktop:~/cam/gspcav1-20071224$ sudo modprobe -v gspca
F

so something has obviously gone wrong!

---

### Post by spiderbatdad on 2009-04-05
you probably dont have the module loaded yet. ```
lsmod
```will show you loaded modules. You'll most likely see uncvideo. That guide is a little difficult. You do have to patch the driver before trying to install it. What exactly are you trying to do, and why do you want the gspca driver?

---

### Post by OllieGab on 2009-04-05
I'm trying to get a LifeCam VX3000 web camera (Microsoft unfortunately) to work and I found a list on the net telling me that I need this driver for that particular camera.

---

### Post by spiderbatdad on 2009-04-05
I did use this guide several months ago and got it working with some effort. I used comments suggeted by sweeper November 14th, 2008 at 1:19 pm...just scroll down.
I eventually unloaded this driver and found a way to make my cam work with skype...if that is your goal:
[http://ubuntuforums.org/showthread.php?t=1026188](http://ubuntuforums.org/showthread.php?t=1026188)

---

### Post by OllieGab on 2009-04-05
I have only done half of it but it did bring up a picture when testing via options i Skype. That's the first time I've actually had a picture at all with this camera - albeit the picture quality being less acceptable. But I'm sure I'm on the right track!

Cheers for that!


Ollie

---

### Post by spiderbatdad on 2009-04-05
I assume you mean running skype with LD_PRELOAD. Glad you had some success. Make sure you have the uvcvideo driver listed under lsmod. Or load it and reboot. If you still want to install the gspca driver on actionshrimp, scroll dwon to sweepers comments for help. Best of luck. Or upgrade to Jaunty Jackalope and you may find the drivers are better than ever.

---

