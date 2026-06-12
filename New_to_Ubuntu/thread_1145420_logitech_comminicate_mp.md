---
title: "logitech comminicate mp"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by DarinB on 2009-05-01
i have no idea what to do other than plug it in,,,on vista that is all i did.
how about jaunty 
here is lsusb 
darin@darin-desktop:~$ lsusb
Bus 001 Device 005: ID 046d:09a1 Logitech, Inc. 
Bus 001 Device 004: ID 03f0:4e11 Hewlett-Packard Photosmart 2570 series
Bus 001 Device 002: ID 05e3:0716 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
darin@darin-desktop:~$

---

### Post by llamabr on 2009-05-01
What have you tried?

```
brock@hops:~$ apt-cache search webcam
came - Rewrite of the xawtv webcam app using imlib2
cameramonitor - Webcam monitoring in system tray
camgrab - A command line tool to download a single image from a webcam
camorama - gnome utility to view and save images from a webcam
camstream - collection of tools for webcams and other video-devices
camstream-doc - documentation for CamStream
feh - imlib2 based image viewer
geekast - GNOME interface to peercast
geekast-binary - GNOME interface to peercast - binaries
gkrellkam - GKrellM plugin that displays a periodically updating image
gmotionlive - A simple multipart/x-mixed-replace viewer
gqcam - GTK Webcam control
gspca-source - source for the gspca v4l kernel module
libdecodeqr-dev - A C/C++ library for decoding QR code
libdecodeqr-examples - Sample program in C/C++ library for decoding QR code
libdecodeqr0 - A C/C++ library for decoding QR code
luvcview - USB Video Class grabber
lynkeos.app - Tool to process planetary astronomical images for GNUstep
motion - V4L capture program supporting motion detection
ov51x-jpeg-source - Source for the ov51x-jpeg driver
peercast-geekast - GNOME interface to peercast - peercast-servent data files
pymissile - Control Marks and Spencer USB Missile Launcher
qc-usb-source - source for the QuickCam Express driver
qc-usb-utils - utility programs for the QuickCam Express driver
setpwc - program to set and query settings of (mainly) Philips WebCams
telak - display remote or local pictures on your desktop
uvccapture - USB UVC Video Class snapshot software
vgrabbj - grabs a image from a camera and puts it in jpg/png format
webcam - image grabber and uploader
webcam-server - a tool to share webcam streaming in www-browser
webcamd - Capture images from video devices
cheese - A tool to take pictures and videos from your webcam
brock@hops:~$ 

```

---

### Post by DarinB on 2009-05-01
what you posted was not clear for a newbie.
also the web cam works with cheese, now how do i make it work with pidgin so i can aim with people

---

### Post by Didius Falco on 2009-05-01
Pidgin doesn't have webcam support at this time, though they plan to add it in.

You may want to try Kopete, which is available in the **Add/Remove** listing. It does have webcam support with some chat networks.  It will work under Gnome, but it is a KDE app, so installing it will likely add a list of packages it needs.

Here is a link to their web page so you can go get more information:

[http://kopete.kde.org/](http://kopete.kde.org/)

I hope this helps...

---

