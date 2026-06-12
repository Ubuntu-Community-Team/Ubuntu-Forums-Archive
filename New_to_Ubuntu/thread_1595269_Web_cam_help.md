---
title: "Web cam help"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by gary2190 on 2010-10-13
Hi. Could you please help me. I have a Novatech V14 laptop running Ubuntu 10.10. But I can not get the web cam to work. I know the hotkey for it is fn+f10, but that does not seem to work either. It will not work on anything I try Skype, Cheese or Google chat. Thanks.

---

### Post by AndyM3 on 2010-10-13
```
sudo add-apt-repository ppa:libv4l
sudo apt-get update
sudo apt-get upgrade
```
Copy-paste that into a terminal (Applications > Accessories > Terminal). Should do the trick, but no guarantees.

---

### Post by gary2190 on 2010-10-14
Tried this but still does not work. I installed camera monitor does not detect web cam. The cam is a bison cam nb pro. Thanks.

---

### Post by no2498 on 2010-10-15
put this in a terminal

lsusb click enter

that will give you the # for your cam ( or should anyway )

try the cam in cheese first 9 out of 10 that can not get a cam going try skype first


lsmod | grep video  click enter


this is my lsmod | grep video

video                  19856  0 
output                  4736  1 video
videodev               29312  1 gspca
v4l2_common            18304  1 videodev
v4l1_compat            15492  1 videodev





gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's


hope 1 of them help

---

### Post by gary2190 on 2010-10-17
Tried it. It brought up what you said and when I tried the gstreamer properties it did not see the web cam did not recognize dev video0. Thanks anyway.

---

### Post by gary2190 on 2010-10-24
Here we go again. I put dmesg in a terminal and the webcam is there, but I get a "no streaming interface" message below it. Is this relevant. Thanks.

---

### Post by no2498 on 2010-10-25
see if this helps put this in a terminal

webcam click enter

---

### Post by gary2190 on 2010-11-02
Hi. I put webcam in a terminal and it came back with.
v4l2: open/dev/video0: No such file or directory.
v4l: open/dev/video0: No such file or directory.
No grabber device available.

If you could tell me what this means and what to do next I would be grateful.

---

### Post by arochester on 2010-11-02
Have you actually installed v4l and v4l2? (That's with an l for lemur NOT 1 as in 1,2,3)

Check in Synaptic to see if they are installed, and if not install them.

---

### Post by gary2190 on 2010-11-02
Checked the synaptic manager and yes they are there.

---

### Post by gary2190 on 2010-11-04
Right. After spending sometime looking for a driver I found one on Sourceforge and downloaded it, which it seemed to do. But the webcam is still not being seen even in Skype. Is there something I am missing or is do I need to do anything else. Please help, getting desperate. Thanks.

---

### Post by Quackers on 2010-11-04
Does Cheese see the webcam now? Does gstreamer-properties?

---

### Post by gary2190 on 2010-11-04
No, still does not see it. When I go into gstreamer-properties and test thru v4l2 and v4l it tells me that Device "/dev/video0 does not exist. I tried with turning on the webcam through fn+10 and then off again. Then Cheese just goes to a blank screen.

---

