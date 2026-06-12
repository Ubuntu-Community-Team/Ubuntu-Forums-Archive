---
title: "fastest way to see if your  webcam is supported"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by no2498 on 2010-01-23
open a terminal type ( gstreamer-properties ) click enter
try v4l1 or v4l2

if it comes on good if not you may need a driver for your cam

if it comes on or not you need a program to use it with like 
cheese,wxcam,xawtv
is a long list of programs to use 1 with
hope this helps a lot of you
john :)

---

### Post by elliotbeken on 2010-01-23
no2498 that is a great little how to thanks worked straight away with my laptop built in camra:P

---

### Post by KarmaJones on 2010-01-28
thanks!

---

### Post by J V on 2010-01-28
Practically all webcams and usb devices work straight off with linux (standards ftw!)

---

### Post by frenchn00b on 2010-01-28
> **no2498 said:**
> open a terminal type ( gstreamer-properties ) click enter
try v4l1 or v4l2

if it comes on good if not you may need a driver for your cam

if it comes on or not you need a program to use it with like 
cheese,wxcam,xawtv
is a long list of programs to use 1 with
hope this helps a lot of you
john :)

or x11 with camorama or :
webcamplayershow.sh
```
mplayer -tv device=/dev/video0 tv://
```

---

