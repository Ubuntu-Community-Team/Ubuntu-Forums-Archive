---
title: "Webcam Security/Motion Capture on Linux?"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by Andy06 on 2009-07-25
Need a good software for using webcam as a security cam. Needs to be able to record video on detecting motion and saving it to hard disk. Most importantly, it should be hassle free and easy to use.

What app/program do you recommend? I had a look at motion but that was waaaaay too hard, needs manual editing of .conf files to get it to work. I need something with a GUI.

Thanks a lot

---

### Post by llamabr on 2009-07-25
What hardware are you using?  I've never successfully set up a webcam, but there's lots of programs:

```
brock@hops:~$ apt-cache search security camera
camstream - collection of tools for webcams and other video-devices
zoneminder - Linux video camera security and surveillance solution
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

### Post by Andy06 on 2009-07-25
Dunno. Never bothered to find out :D

How to find out on Linux? IIRC when I had windows it would show up as Ricoh or Chicony in Device manager. In the Device manager app on GNOME, its just a question mark. Works though. Checked with Cheese.

---

### Post by ly9000 on 2010-11-24
High quality video security with Ubuntu desktop 10.10, Zoneminder 1.24.x and webcam. This link may be help you:

[http://www.howtoforge.org/forums/showthread.php?t=50199](http://www.howtoforge.org/forums/showthread.php?t=50199)

Gook luck!

---

### Post by HermanAB on 2010-11-24
Zoneminder or Motion.

---

### Post by mastablasta on 2010-11-24
> **ly9000 said:**
> High quality video security with Ubuntu desktop 10.10, Zoneminder 1.24.x and webcam. This link may be help you:
 
[http://www.howtoforge.org/forums/showthread.php?t=50199](http://www.howtoforge.org/forums/showthread.php?t=50199)
 
Gook luck!
 
wow. so much work for such a task....
 
still, i might give this a try. would be an interesting experiment.
 
a bit dissapointing for linux again... - in windows you would get such a programme together with cam and they are usually really easy to set up.

---

### Post by felixq78 on 2011-04-30
> **mastablasta said:**
> wow. so much work for such a task....
 
still, i might give this a try. would be an interesting experiment.
 
a bit dissapointing for linux again... - in windows you would get such a programme together with cam and they are usually really easy to set up.

Yes but there's a trade off for that ease of use that Windo$e has, 
                                                   VULNERABILITY !
It's so much easier for spyware applications, port attacks etc  when your system is so easy to use for you it's also just as easy for some remote application or hacker to just walk in and do their best.
Linux is harder to penetrate remotely because you need to use command lines passwords etc etc. removing the need for anti-virus/spyware, apps.
Linux is way more stable too.:guitar:

---

### Post by mrbrutal on 2012-03-29
I use Xeoma for Linux edition, flawless so far. google it if you need easy software with the full functionality of win apps

---

