---
title: "How do I get Ubuntu to recognize my webcam?"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by markd79 on 2010-05-26
[B]Hi,

I have a Toshiba Satellite L505-S5993 with built in webcam.  I am running ubuntu 10.04 through virtual box on my Windows 7 machine.  However my webcam is not recognized?  I looked for linux drivers for the webcam but have not found any.  Does anyone have any solutions?

Also when I try to use Rhythmbox music player (and also with Skype) my sound output is very patchy.... I hear it for a few seconds and then it switches off and back on in a while. Has anyone encountered this problem and fixed it?

Thanks in advance,

Mark
[/B]

---

### Post by -humanaut- on 2010-05-26
I'm fairly certain webcams won't be seen by "Virtual Box" try typing lspci in a terminal and see if it's even there.

---

### Post by no2498 on 2010-05-26
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

910 and up cheese webcam booth is loaded
look in sound & video

try the cam in cheese

most all webcam's use v4l drivers

hope this helps

---

### Post by markd79 on 2010-05-26
You are right.  It does not seem to be there.  So this is just an issue with Virtual Box then and therefore can't be fixed?

Any ideas about the audio issue?

Thanks very much for your help.

---

### Post by markd79 on 2010-05-26
> **no2498 said:**
> open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

910 and up cheese webcam booth is loaded
look in sound & video

try the cam in cheese

most all webcam's use v4l drivers

hope this helps

I tested both and got the message: 
Video for Linux (v4l): Device "/dev/video0" does not exist

Cheese does not detect the camera

---

### Post by QIII on 2010-05-26
Are you running the Open Source Virtualbox, or the PEUL version?

I'm not sure how things might work on a Windows host, but the OSE version has several limitations -- USB access being one of them.

The PEUL version may give you access to your host's hardware.

---

### Post by no2498 on 2010-05-26
you do this yet  im not sure if you can

sudo apt-get install ubuntu-restricted-extras


gstreamer also needs the good,bad,ugly installed

you can find them in the add/remove program

---

### Post by dunbrokin on 2010-06-01
My Webcam is not detected under 10.04..it worked perfectly under 9.10 (but I do not remember what I had to do to get it to work!!). Where should I start?

---

