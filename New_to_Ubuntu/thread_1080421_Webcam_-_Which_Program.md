---
title: "Webcam - Which Program?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by BruisedQuasar07 on 2009-02-25
I'd like to get a pretty standard GE EasyCam running in Ubuntu Linux. I looked around in the standard Ubuntu 8.10 supplied multimedia programs beginning with Xsane. No go, as far as I could see.

What is a good Ubuntu ready program to try to get the cam running? The light comes on but I haven't been able to operate it or get any video recording. I don't want to anything fancy beyond basic capture to the Desktop.

--Bruised

---

### Post by llamabr on 2009-02-25
I've fought with mine for a while, too, but never had any luck.  You can start with these:

```
brock@vader:~$ apt-cache search webcam
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
brock@vader:~$ 


```

---

### Post by binbash on 2009-02-25
cheese is a good one

---

### Post by Temposs on 2009-02-25
Yeah, try out Cheese. It's very simple, basically what you want.

---

### Post by alexandari on 2009-02-25
yea i`m using cheese too and it rocks

---

### Post by BruisedQuasar07 on 2009-02-25
Thank you everyone. I looked over the description for cheese but I wasn't sure what it does. I'll try it. My grand children will probably be thrilled with it.

--Bruised

---

