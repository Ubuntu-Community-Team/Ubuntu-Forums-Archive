---
title: "Webcam works under camorma, but no where else..."
date: 2009-09-18
forum: New to Ubuntu
---

### Post by Li18nxBoy on 2009-09-18
```
:~$ lsusb
Bus 005 Device 005: ID 046d:0870 Logitech, Inc. QuickCam Express

:~$ ls /dev/video*
/dev/video0
```

I cycled thew all the gstreamer-properties setting:

```
:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(198): gst_v4l_open (): /GstPipeline:pipeline6/GstV4lSrc:v4lsrc2:
Device opened, but wrong type (0x0)]
libv4l2: error getting capabilities: Unknown error 515
libv4l2: error getting capabilities: Unknown error 515
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error getting capabilities for device '/dev/video0': It isn't a v4l2 driver. Check if it is a v4l1 driver. [v4l2_calls.c(95): gst_v4l2_get_capabilities (): /GstPipeline:pipeline7/GstV4l2Src:v4l2src2:
system error: Unknown error 515]
libv4l2: error getting capabilities: Unknown error 515
gstreamer-properties-Message: Error running pipeline 'Custom': Error getting capabilities for device '/dev/video0': It isn't a v4l2 driver. Check if it is a v4l1 driver. [v4l2_calls.c(95): gst_v4l2_get_capabilities (): /GstPipeline:pipeline8/GstV4l2Src:v4l2src3:
system error: Unknown error 515]
```


Any idea what the problem is?

---

### Post by Li18nxBoy on 2009-09-20
*bumpage

---

### Post by no2498 on 2009-09-21
did you get a popup window
click video try v4l or v4l2

---

### Post by Li18nxBoy on 2009-09-21
I did, it was no good :(

---

### Post by Li18nxBoy on 2009-09-21
Does camorama not use gstream?

---

### Post by Li18nxBoy on 2009-10-04
bump

---

### Post by Li18nxBoy on 2009-10-05
*bump

---

