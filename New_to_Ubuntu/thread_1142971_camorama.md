---
title: "camorama"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by taith on 2009-04-29
hello,

i'm having issues with camorama since the 9.04...

> $ camorama -d=/dev/video1 -D

VIDIOCGCAP
device name = CIF Single Chip     
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 352
max height = 288
min width = 48
min height = 32

VIDIOCGWIN
x = 0
y = 0
width = 176
height = 144
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 176
height = 144
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 1028
hue = 0
colour = 0
contrast = 0
whiteness = 0
colour depth = 8

VIDIOCGMBUF
mb.size = 409600
mb.frames = 4
mb.offset = 102400
update_tooltip called
tip - acap off
** Message: SET PIC
update_tooltip called
tip - acap off
Unable to capture image (VIDIOCSYNC)


as such... the program will not show a picture of any sort... "Unable to capture image" and closes...

---

### Post by gandaran on 2009-04-29
is it just with camorama?
I don't think its a camorama problem, most likely camera driver problem , my camera doesn't work with any application in jaunty and intrepid, used to work more or less okay in hardy, camera support in linux is very bad.
> Bus 003 Device 003: ID 046d:092b Logitech, Inc. Labtec WebCam Plus


---

### Post by taith on 2009-04-29
i just installed cheese... program starts, as soon as i switch to video1(i have a tv tuner as video0) the program freezes

---

### Post by krcabrer on 2009-05-12
I got the same problem...

Is there any solution for the webcam in the new Ubuntu version?

Thank you very much.

Kenneth

---

### Post by zasq on 2009-07-19
Hi!
Has anyone found a solution? Skype and Cheese work for me, but camorama doesn't. Must be a v4l2-Problem...
Any help appreciated, because camorama used to be the best of the webcam apps.
Thank you!

---

### Post by ubot on 2009-08-23
I have found a solution.  In Ubuntu 8.10+ they finally implemented the superior v4l2 api.  However, any app using v4l suddenly stopped working.  Here is what I did to get it working:

1) Make sure libv4l is up to date  (go in synaptic and look it up)

2) You need to set LD_PRELOAD to your v4l1compat.so library and run camorama

```
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
camorama 
```

This worked for me

---

### Post by PC_load_letter on 2009-10-19
Thanks! Fixed Camorama for me on my Dell Vostro 1400 which only worked with Cheese.

---

### Post by malefisocu on 2009-10-23
> **ubot said:**
> I have found a solution.  In Ubuntu 8.10+ they finally implemented the superior v4l2 api.  However, any app using v4l suddenly stopped working.  Here is what I did to get it working:

1) Make sure libv4l is up to date  (go in synaptic and look it up)

2) You need to set LD_PRELOAD to your v4l1compat.so library and run camorama

```
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
camorama 
```

This worked for me
Thank you Ubot. Your advice allowed me to make camorama work. But I'm still having trouble with Skype. My cam worked ok with Xawtv and with Cheese, but not with Caorama nor Skype. Any other tip?

---

### Post by arvevans on 2009-10-24
OK.  "export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so"  fixed my problem with "cannot open /dev/video0" popup window.

However, picture has 1 image and another 1/2 image to the right of it. 
Resolution is also very low.

Thanks for helping resolve the "inability to open /dev/video0 problem.
Now on to try fixing the video fold and resolution.
_._

UPDATE:  Reboot fixed the video fold (1 plus 1/2 image).  Resolution is still low for a 12 megapixel camera

---

### Post by davemar on 2009-10-25
How did you fix the 1 + 1/2 picture problem? I've got the same problem with mine, plus it's monochrome with vertical bars.

---

### Post by arvevans on 2009-10-25
Davemar

My 1-and-a-half-image problem went away with a reboot.
I have no idea what the problem, or the real solution, might have been.

Now, only problem is why my 12 megapixel camera is only supported to 320 X 160 image density?

Arv
_._

---

### Post by no2498 on 2009-10-27
try getting the program
wxcam 

i think it works better than cheese

also try the 

gstreamer-properties

in the terminal

try the video diff ones for the best pic

---

