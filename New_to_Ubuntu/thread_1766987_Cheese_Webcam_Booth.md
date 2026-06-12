---
title: "Cheese Webcam Booth"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by MMul on 2011-05-25
I have just moved to 11.04. When I try to start Cheese from the terminal, I get the following message.

mm@:~$ cheese

Gtk-ERROR **: List item does not match its index: item index 93 and list index 92

aborting...
Aborted
mm@:~$ 


What is happening here and what should I do.

Thanks

---

### Post by trozamon on 2011-05-25
You could try this: 
 
```
 
sudo apt-get --purge remove cheese
sudo apt-get install cheese

```
 
This might work.

---

### Post by MMul on 2011-05-25
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video1' cannot capture at 1280x960 [gstv4l2object.c(2093): gst_v4l2_object_set_format (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
Call to S_FMT failed for YUYV @ 1280x960: Input/output error]


But my device is not set up under preferences to capture 1280x960?!?

---

### Post by MMul on 2011-05-25
> **trozamon said:**
> You could try this: 
 
```
 
sudo apt-get --purge remove cheese
sudo apt-get install cheese

```This might work.


Thanks I will try that...

No difference I am afraid...

---

### Post by no2498 on 2011-05-26
try this program wxcam
it was in the package manager i do not know if it still is
you can get it in a deb file you may need to try different ones to get 1 that loads 

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

---

