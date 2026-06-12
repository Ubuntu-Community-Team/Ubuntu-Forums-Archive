---
title: "have Camorama and web cam still not detected"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by cheekymonky2010 on 2010-09-02
Could anyone please help with suggestions on how to get my web cam to work on Linux????  It works on cheese but not online please help?????

---

### Post by ibizatunes on 2010-09-02
do a lsusb, and post that,
google webcam and ubuntu

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

what app are you trying to run it on?

---

### Post by cheekymonky2010 on 2010-09-02
Internet web cam chat rooms

---

### Post by cheekymonky2010 on 2010-09-02
What is an ISUB please?

---

### Post by no2498 on 2010-09-03
he wants you to type this in a terminal lsusb click enter

---

### Post by bredman on 2010-09-03
Hold down CTRL ALT and t to open a terminal
Type in the command
lsusb

If you find a line referring to a webcam, tell us what this line says.

This will give us the type of webcam, so we can help you.

---

### Post by bredman on 2010-09-03
I figured out that you probably have a Genius Eye 312 (093a:2622) by reading your other posts.

If this is the case, I recommend that you enter the following commands in a terminal

sudo add-apt-repository ppa:libv4l
sudo aptitude update
 sudo aptitude full-upgrade


What these commands do:
1. Add the unofficial "Video for Linux" libraries to your software collection.
2. Rebuild your software list
3. Get all the latest software available (including v4l)


Note, if you are not already on Ubuntu 10.04, this will upgrade you to 10.04. If you don't want to do this, let us know.

---

