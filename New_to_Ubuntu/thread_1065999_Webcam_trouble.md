---
title: "Webcam trouble"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by CujoHatesWebcams on 2009-02-10
I have been trying for jeez, 2 hours to get this webcam to work:
It is a no-brand camera, from soyntec(y), apparantly a "Joinsee™ 110" (the most comforable way to videoconference). 

lsusb reads it as 
Bus 002 Device 004: ID 06a2:6810 Topro Technology, Inc. 

Every single attempt to make it work gives me the error (this one is from gstreamer-properties 

```
cujo@cujo-laptop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline0/v4lsrc3]

```
that is trying to use v4l.
trying v4l2

```
caleb@cujo-laptop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device "/dev/video0". [v4l2_calls.c(429): gst_v4l2_open (): /pipeline0/v4l2src2:
system error: No such file or directory]

```

ls /dev/vid* comes back with "no such file or directory".

I tried innumerable things, specifically trying UVC, qc-usb, and so many other things :( as you can see, nothing worked.

It is registered by the USB, but as I said there's no /dev/video0 or video1 or any video at all :(

any help at all would be appreciated.

---

### Post by Temposs on 2009-02-10
hi Cujo,
   Which version of Ubuntu are you using?

---

### Post by CujoHatesWebcams on 2009-02-10
I think it's Ubuntu 8.10, but it might be 8.04

uname -a returns:
Linux cujo-laptop 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux

---

### Post by cariboo on 2009-02-10
Could you tell us if the correct module is loading?

In a terminal type:

```
lsmod | grep spca 
```

Jim

---

### Post by Temposs on 2009-02-10
> **CujoHatesWebcams said:**
> I think it's Ubuntu 8.10, but it might be 8.04

uname -a returns:
Linux cujo-laptop 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux

For the record, you have Ubuntu 8.04.

For what it's worth, it's easier to get webcams to work in 8.04 than in 8.10 :-)

---

### Post by CujoHatesWebcams on 2009-02-10
> **cariboo907 said:**
> Could you tell us if the correct module is loading?

In a terminal type:

```
lsmod | grep spca 
```

Jim
That returned nothing, could that be the problem?

---

### Post by Berduchwal on 2009-05-16
There is new kernel patch for this webcam:

[http://patchwork.kernel.org/patch/16936/](http://patchwork.kernel.org/patch/16936/)

I am currently trying to apply it.

---

