---
title: "no /dev/video for my supported usb webcam?"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by niffcreature on 2010-02-02
hi i have a sony z, the camera has worked out of box for everyone but me. it shows up and the driver is installed (i think). does not work with ekiga, cheese, amsn, skype etc. i have tried to use MKNOD to make /dev/video with this command: "mknod /dev/video0 c 81 0"...
lsusb:
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 044e:3017 Alps Electric Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1410:2120 Novatel Wireless 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 147e:1000  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

the first device is the camera as listed here [http://www.basyskom.org/~eva/log_installation_vaio_z21vnx.html](http://www.basyskom.org/~eva/log_installation_vaio_z21vnx.html)

i AM using the sony laptop module, which apparently can control some things about the webcam, i dont know what. more strange results:

v4l-conf: using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1600x900, depth=24, bpp=32, bpl=6400, base=unknown
can't open /dev/video0: No such file or directory

gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline1/GstV4lSrc:v4lsrc2]

anyone know anything? help would be greatly appreciated. thanks

---

