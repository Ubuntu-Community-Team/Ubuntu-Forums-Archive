---
title: "Driver for my video camera?"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by Mikey Teh Zombe on 2010-04-19
i need this driver so i can use my video camera as a webcam,
[http://www.samsung.com/us/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=04021100&prd_mdl_cd=SC-MX10%2FXAA&prd_mdl_name=SC-MX10&prd_ia_sub_class_cd=P](http://www.samsung.com/us/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=04021100&prd_mdl_cd=SC-MX10%2FXAA&prd_mdl_name=SC-MX10&prd_ia_sub_class_cd=P)

how would i install this?

---

### Post by Mikey Teh Zombe on 2010-04-19
bump

---

### Post by Mikey Teh Zombe on 2010-04-19
bump

---

### Post by Mikey Teh Zombe on 2010-04-19
Bump!!!!

---

### Post by RedRat on 2010-04-19
That driver is for Windows and not Linux. If you are running Ubuntu, install Wine or use a VM. While I can hook up my Canon video camera and see video using the various video editing tools, as a web-cam I don't know. To be honest, I had not thought about using the camera in that way. 

Off the top of my head, I would think that the video stream would be quite large compared to a web-cam, most have limited bandwidth and resolution, but I am no expert here. Perhaps someone else could chime in. 

Why not just buy an inexpensive web-cam, Logitech makes them, and they can be had for under $100 nowadays. I believe Ubuntu recognizes them, at least the web-cams that are supported.

---

### Post by lisati on 2010-04-19
What happens when you plug your camera in and turn it on? Ubuntu is able to read from some cameras without the need for additional drivers.

(And try not to bump your thread more than once every 24 hours)

---

### Post by Mikey Teh Zombe on 2010-04-19
> **lisati said:**
> What happens when you plug your camera in and turn it on? Ubuntu is able to read from some cameras without the need for additional drivers.

(And try not to bump your thread more than once every 24 hours)

nothing happens when i set pc cam like literally nothing happens..
no beeps or pop up windows

---

### Post by cariboo on 2010-04-19
If your camera has a DV connector, use firewire, my Sony Digital Handy Cam works out of the box connected via firewire.

**Edit: Please don't bump your thread until 24 hours has elapsed**

---

### Post by Mikey Teh Zombe on 2010-04-19
> **cariboo907 said:**
> If your camera has a DV connector, use firewire, my Sony Digital Handy Cam works out of the box connected via firewire.

**Edit: Please don't bump your thread until 24 hours has elapsed**

i do not have firewire

---

### Post by no2498 on 2010-04-20
plug the cam in turn it on
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

910 and up cheese is loaded
try the cam in cheese

hope this helps

---

