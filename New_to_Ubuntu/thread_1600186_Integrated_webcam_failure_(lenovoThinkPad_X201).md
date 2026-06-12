---
title: "Integrated webcam failure (lenovoThinkPad X201)"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by prisae on 2010-10-18
Hello folks,

I bought a new lenovo ThinkPad X201 some months ago, and installed Ubuntu 10.04. Everything worked fine, including the integrated webcam. Sometimes in August it failed to work, in skype as well as in cheese or in guvcview. External USB cameras still worked though. So I used my external and waited patiently for Ubuntu 10.10, hoping it would work then. Unfortunately not. None of the tricks I found in forums like this helped.

**Problem:** Integrated webcam is not working, not in skype nor in cheese or guvcview. However, all of them recognize that there is a camera, meaning I can choose it *Integrated Camera (/dev/video0)*. But there is nothing happening, black screen, and the LED next to the Integrated Camera never starts working any more. USB cameras still work fine though.

**Question:** Is it possible that an integrated camera is not properly mounted or broken? How could I find out?

This is the output of lsusb:
```

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 093a:2622 Pixart Imaging, Inc. 
Bus 001 Device 005: ID 17ef:4816 Lenovo 
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I give here some output of guvcview if run from a terminal, which might be of any help:
```

~/> guvcview
guvcview 1.4.1
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
/dev/video0 - device 1
/dev/video1 - device 2
Init. Integrated Camera (location: usb-0000:00:1a.0-1.6)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30,

*... many lines with similar output ...*

{ discrete: width = 1600, height = 1200 }
    Time interval between frame: 1/15, 
vid:17ef 
pid:4816 
driver:uvcvideo
checking format: 1196444237
VIDIOC_G_COMP:: Invalid argument
   compression control not supported
fps is set to 1/30
drawing controls

fps is set to 1/30
no codec detected for H264
no codec detected for MP3 - (lavc)
 Could not grab image (select timeout): Resource temporarily unavailable

*=> this line repeats on and on*

```

Note:
/dev/video0 - device 1 -> Integrated Camera
/dev/video1 - device 2 -> An USB webcam

Any help or ideas would be highly appreciated! I am happy to provide more information if needed.

Thanks a lot in advance

---

### Post by robsoles on 2010-10-18
Welcome to UF.

Sorry to say that I think your internal webcam is broken and the only way of proving it beyond a doubt is to get drivers in an OS that can 'manage' it and trying it thoroughly - I think you've done that and the fact that the LED next to it no longer lights up is a bad sign.

I would try it off a LiveCD and as a last resort I might even try to get an alternative hard drive and install Windows temporarily to it to prove that the camera doesn't happen to go for that OS either.

---

### Post by prisae on 2010-10-19
Thanks for your reply robsoles.

Unfortunately the answer I feared. Well, will probably wait until I have my work laptop, and then send in my private one, as I am having a 3 yr guarantee on it. Still a pain though.

Unless somebody else has a bright idea!

---

### Post by no2498 on 2010-10-19
unplug the usb cam 
restart the computer
try the cam
if it dont come on try this

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by prisae on 2010-10-19
Thanks for the input.

I won't unplug the Camera, as it is an Integrated Camera (and I am pretty sure they would decline the warranty thereafter).

I already tried the gstreamer-properties, with the same result as with cheese or guvcview as well: not working. v4l2: I can choose *Device: Integrated Camera*. It says testing, but now video appears. v4l: I can't choose any device.

---

### Post by robsoles on 2010-10-19
Glad to hear warranty is good. I wish you had a separate hard drive you could pop in it with Windows on for the people who will be looking at the webcam, computer shops and repair centres can be a menace when it comes to Linux.

---

### Post by prisae on 2010-10-19
You might be right there. Although I ordered the laptop from lenovo officially without OS. So they should be able to fix it anyhow. They can put on my disk what ever they wish, and I can put back on my system thereafter.

Thanks again.

---

### Post by no2498 on 2010-10-19
Note:
/dev/video0 - device 1 -> Integrated Camera
/dev/video1 - device 2 -> An USB webcam


that says you have 2 cams

---

### Post by no2498 on 2010-10-19
just reread your output

no codec detected for H264
no codec detected for MP3 - (lavc)


the fast way to get the 264 code is install smplayer
type smplayer in a terminal it tells you how to install it

---

### Post by prisae on 2010-10-19
Sorry no2498, of course you were right, there were two cameras, one of them USB. But this one worked and was just to test if other cameras do work. The problem is the integrated one.

I tried it with the smplayer, but it did not change anything, unfortunately. Thanks for the hint anyway.

---

### Post by no2498 on 2010-10-20
with the usb cam unpluged
open a terminal type webcam click enter whats it say

then retry 

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by prisae on 2010-10-20
*webcam* was not installed, so I installed it. Then it says
```

~/> webcam
reading config file: /home/dtr/.webcamrc
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [none]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320

```

When I try gstreamer-properties there is the same as always:
- v4l: I can't choose any device
- v4l2: I can choose *Device: Integrated Camera*. It says testing, but now video appears

Thanks for your continuing help!

---

### Post by prisae on 2010-11-22
Just to round off this thread: The internal webcam was broken indeed. I  sent it to the repair centre, and it is fixed now, everything is fine  again!

Thanks for your support.

---

