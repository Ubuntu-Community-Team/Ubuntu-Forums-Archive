---
title: "How do I make and install downloaded file for drivers"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by Dennis Roth on 2009-09-21
Hey, I've just got through downloading files for a webcam driver and can't work out how to get the 'make' command to work, if someone could explain it in really simple terms that'd be awesome. Thanks in advance!

Dennis.

---

### Post by sisco311 on 2009-09-21
Hi and welcome to the forums!!!

Do you really need to compile the driver from source? 

Please post a link to the driver and your webcam type.


[http://psychocats.net/ubuntu/installingsoftware]("http://psychocats.net/ubuntu/installingsoftware")

[https://help.ubuntu.com/community/CompilingSoftware]("https://help.ubuntu.com/community/CompilingSoftware")

---

### Post by Dennis Roth on 2009-09-21
This is the link I got the driver from, but its really just a bunch of files to me,
[http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/](http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/)

As for the webcam, its a logitech quickcam, I think, got it ages ago and lost the install disk.

Sorry if thats a bit vague...

---

### Post by sisco311 on 2009-09-21
Your Webcam is probably detected and the driver loaded.

Do you have any software installed to see if it's detected.
(skype, ekiga, mplayer, xawtv...)

Open a terminal (Applications -> Accessories -> Terminal)
run the following commands and post the output:
```
lsusb
```
```
lsmod
```
or
```
ls -al /dev/video*
```

---

### Post by Dennis Roth on 2009-09-21
I used the lsusb command and got this,

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:092c Logitech, Inc. QuickCam Chat
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Good or bad?

---

### Post by ajgreeny on 2009-09-21
If your version of ubuntu has cheese in the repos install that and run it.  You may be surprised to see that the camera already works.

---

### Post by Dennis Roth on 2009-09-21
Aw man I feel so slow, how would I do that?

---

### Post by sisco311 on 2009-09-21
> **Dennis Roth said:**
> Aw man I feel so slow, how would I do that?

Go to Applications -> Add/Remove, search for *cheese* and install it. :)

Step by step instruction:
[http://psychocats.net/ubuntu/installingsoftware]("http://psychocats.net/ubuntu/installingsoftware")

---

### Post by Dennis Roth on 2009-09-21
Ok, all seems to be working except for webcam feature on aMSN just shows a white space for the reciever...

---

### Post by sisco311 on 2009-09-21
Did you set up the cam in amsn?

Account -> Preferences -> Others tab -> Edit Audio and Video settings.

---

### Post by Dennis Roth on 2009-09-21
Did that, still just white...

Any ideas why?

---

