---
title: "webcam issues."
date: 2009-02-16
forum: New to Ubuntu
---

### Post by 0m6 on 2009-02-16
hello.  ive recently switched to linux mint. i have someone trying to coach me through some of the things i should know or do. but i cant get my webcam to work.
marley@SpaceToast ~ $ lsusb
Bus 005 Device 011: ID 03f0:5e11 Hewlett-Packard Photosmart D7400 series
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 093a:2621 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
marley@SpaceToast ~ $

---

### Post by cariboo on 2009-02-17
If you are using 8.10 or later, the driver for your webcam is loaded automatically, open a terminal and type:

```
lsmod | grep spca
```

you should get a result something like this:

```
lsmod | grep spca
gspca_zc3xx            59392  0 
gspca_main             34560  1 gspca_zc3xx
compat_ioctl32         18304  2 saa7134,gspca_main
videodev               45184  4 tuner,saa7134,gspca_main,compat_ioctl32
```

ignore the entry for saa7134 as that is my tv tuner card.

Install xawtv, it is in the repositories, you can use synaptic to install it, then open a terminal and type:

```
xawtv -c /dev/video0
```

You should now be able to see yourself.

Jim

---

### Post by 0m6 on 2009-02-17
marley@SpaceToast ~ $ xawtv -c /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-7-generic)
xinerama 0: 1600x1200+0+0
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
v4l2: waiting for a free buffer


its been stuck on waiting for a free buffer for a while now. im not sure if thats to be expected or not.

---

### Post by 0m6 on 2009-02-17
nevermind |D i got it.

---

