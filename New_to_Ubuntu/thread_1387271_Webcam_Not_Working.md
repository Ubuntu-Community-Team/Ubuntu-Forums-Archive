---
title: "Webcam Not Working"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by Sparty26 on 2010-01-21
Hello, I need help with my webcam. The camera is a Microsoft LifeCam VX-3000, my computer a Gateway 7330 GZ. when I run lsusb, it shows that the camera is attached, but the camera is not being recognized by Skype (Skype tells me "there are no video devices"). I have tried sifting through the countless pages of threads on this topic to find an answer, but I have not yet come up with one. Any help is greatly appreciated! thank you for your time!

-Adam

---

### Post by Sparty26 on 2010-01-21
.bump.

---

### Post by Sparty26 on 2010-01-21
.double BUMP?.

---

### Post by Kafubie on 2010-01-21
Triple BAMP!:popcorn:

---

### Post by lyall on 2010-01-21
see the following link
[http://ubuntuguide.org/wiki/Ubuntu:Karmic]("http://ubuntuguide.org/wiki/Ubuntu:Karmic")
then scroll down to **4.16 WebCams**

See the Ubuntu webcam guide for more info.
in the section

good luck and have fun learning

---

### Post by zazootheparrot on 2010-09-05
> **Sparty26 said:**
> Hello, I need help with my webcam. The camera is a Microsoft LifeCam VX-3000, my computer a Gateway 7330 GZ. when I run lsusb, it shows that the camera is attached, but the camera is not being recognized by Skype (Skype tells me "there are no video devices"). I have tried sifting through the countless pages of threads on this topic to find an answer, but I have not yet come up with one. Any help is greatly appreciated! thank you for your time!

-Adam

I have exactly the same issue with my webcam (motion eye). When I type in lsusb in shows that it is recognised but it doesn't work with skype. The same with the microphone! :(

I have a sony vaio VGN-SZ740 with Ubuntu 10.04.

Would appreciate any help :)

---

### Post by zazootheparrot on 2010-09-06
bump?

---

### Post by gradinaruvasile on 2010-09-06
Have you guys tried launching skype with

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

in a terminal? (this path is for 32-bit OS - the 64 bit Ubuntu has slightly different path, google for it)

A good test is launching gstreamer-properties (press alt+f2, type the command, press enter) - if you can test the webcam from the video tab, the drivers are ok and Skype needs the aforementioned workaround (works for me on a gspca webcam).
If it doesnt works there, then most likely it wont on other programs and some googling is required.

---

### Post by zazootheparrot on 2010-09-06
> **gradinaruvasile said:**
> Have you guys tried launching skype with

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

in a terminal? (this path is for 32-bit OS - the 64 bit Ubuntu has slightly different path, google for it)

A good test is launching gstreamer-properties (press alt+f2, type the command, press enter) - if you can test the webcam from the video tab, the drivers are ok and Skype needs the aforementioned workaround (works for me on a gspca webcam).
If it doesnt works there, then most likely it wont on other programs and some googling is required.

Tried launching skype using the code you've just mentioned. The webcam is still not working ](*,)
You also mentioned launching gstreamer-properties by pressing alt+f2. What should I type afterwards?

Thanks

---

### Post by gauravj on 2010-09-07
Hi

Borrow your friends web cam and try. See if the problem persists with other web cams or not.
The system is not able to create video device for the web cam.
So way out will be to have another supported web cam for quick solution.
Configuring this one is other solution but i guess stuff isn't 
available on net for this.

---

### Post by aspiredfang on 2010-09-07
A similar thing here with a built in webcam. Issue was resolved after installing the "restricted-extras" package from repository for me. 

Have you got this installed already?

---

### Post by zazootheparrot on 2010-09-07
Just to add that mine's a built-in webcam and according to the result of lsusb it is recognised but still doesn't work:
```
Bus 007 Device 002: ID 044e:3017 Alps Electric Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 054c:0281 Sony Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 003: ID 05ca:183a Ricoh Co., Ltd Visual Communication Camera **VGP-VCC7 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by zazootheparrot on 2010-09-07
> **aspiredfang said:**
> A similar thing here with a built in webcam. Issue was resolved after installing the "restricted-extras" package from repository for me. 

Have you got this installed already?

Did what you just said, still now working :(

Any suggestions?

thx

---

### Post by no2498 on 2010-09-07
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by aspiredfang on 2010-09-07
Sorry the solution I just suggested didn't work :o

Just rereading what has been suggested already, rewinding to [gradinaruvasile]("http://ubuntuforums.org/member.php?u=589640") suggestion and having a poke around:

rather than just typing the following in a terminal - > LD_PRELOAD=/usr/lib/libv4l/v4l1compat.sodid you add "export" before it? So, it would now be> export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so This forces the webcam in to 32-bit mode which was needed before a 64-bit version of Skype was available. note there is now a 64-bit version of skype so the above hack shouldn't really be required in the first place these days. 

I did manage to find under the ubuntu wiki page (linked further down post) about skype the following piece of soft you will need with the ricoh camera though. If you would like to jump straight there rather than find it on the wiki page
[http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)

I'm not so in to the hardware side of Linux at the moment so, cannot really help other than recommending two other links. Best of luck and remember to post your solution should you reach one!

Ubuntu skype wiki
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

There has been an ongoing discussion with issues regarding nix and skype here also
[http://ubuntuforums.org/archive/index.php/t-914952.html](http://ubuntuforums.org/archive/index.php/t-914952.html)

---

### Post by zazootheparrot on 2010-09-18
> **no2498 said:**
> open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's


Tried what you said, the following appeared :
```
root@ava-laptop:~# gstreamer-properties 
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc1]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
system error: No such file or directory]

```

Any ideas what to do next?

---

### Post by zazootheparrot on 2010-09-18
> **aspiredfang said:**
> Sorry the solution I just suggested didn't work :o

Just rereading what has been suggested already, rewinding to [gradinaruvasile]("http://ubuntuforums.org/member.php?u=589640") suggestion and having a poke around:

rather than just typing the following in a terminal - did you add "export" before it? So, it would now beThis forces the webcam in to 32-bit mode which was needed before a 64-bit version of Skype was available. note there is now a 64-bit version of skype so the above hack shouldn't really be required in the first place these days. 

I did manage to find under the ubuntu wiki page (linked further down post) about skype the following piece of soft you will need with the ricoh camera though. If you would like to jump straight there rather than find it on the wiki page
[http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)

I'm not so in to the hardware side of Linux at the moment so, cannot really help other than recommending two other links. Best of luck and remember to post your solution should you reach one!

Ubuntu skype wiki
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

There has been an ongoing discussion with issues regarding nix and skype here also
[http://ubuntuforums.org/archive/index.php/t-914952.html](http://ubuntuforums.org/archive/index.php/t-914952.html)

Tried the code. Nothing actually happened! :( 

please help!!

---

