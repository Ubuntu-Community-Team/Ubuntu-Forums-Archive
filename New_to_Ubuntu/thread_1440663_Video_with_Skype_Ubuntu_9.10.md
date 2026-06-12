---
title: "Video with Skype Ubuntu 9.10"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by alexawkward on 2010-03-27
How do I get video chat to work with skype?

I have a webcam in my computer, i'm not sure if it just doesn't recognize it or what, or how to check the hardware on my system.

Tips?

---

### Post by spiderbatdad on 2010-03-27
which version of Ubuntu? Which version of skype...where did you get it?
These commands in your terminal will help determine if the wbcam is working ok
```
lsusb
lsmod
```
You can paste the results into another post here...inside code tags please...the little # symbol in the window editor.

---

### Post by alexawkward on 2010-03-27
as the title says, it's 9.10.  and it's skype 2.0

---

### Post by spiderbatdad on 2010-03-27
sorry missed that in the title....um I can't see bold.
There are presently 2 versions of skype offered on their site:
hardy_2.1.0.47... and
intrepid_2.1.0.87...
both are deb files. I would recommend uninstalling what you have via synaptic package manager and obtaining intrepid_2.1.0.87...deb from:
[http://www.skype.com/intl/en/download/skype/linux/choose/?gclid=CPr2vOCS2qACFVk65QodETMuAQ&cm_mmc=PAIDS%257CGAWS-_-AMERC%257CUS%257CEN-_-BD%257CSTRCT-_-zf0gn2](http://www.skype.com/intl/en/download/skype/linux/choose/?gclid=CPr2vOCS2qACFVk65QodETMuAQ&cm_mmc=PAIDS%257CGAWS-_-AMERC%257CUS%257CEN-_-BD%257CSTRCT-_-zf0gn2)

---

### Post by no2498 on 2010-03-28
this may or may not help with skype but will help you see the webcam

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese and ekiga softphone are loaded try thr cam in them

hope this helps

---

### Post by nutsy.ben on 2010-04-04
Install first with the package  'Cheese' ... 
 Check if your webcam works correctly...



then check this up [http://ubuntuforums.org/showthread.php?t=1318506](http://ubuntuforums.org/showthread.php?t=1318506)

export XLIB_SKIP_ARGB_VISUALS=1 && skype is the solution !!!

---

