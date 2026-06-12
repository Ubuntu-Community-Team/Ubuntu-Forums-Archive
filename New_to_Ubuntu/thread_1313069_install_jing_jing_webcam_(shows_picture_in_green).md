---
title: "install jing jing webcam (shows picture in green)"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by medya on 2009-11-03
guys I have a usb jingjing webcam and ubuntu 9.10
I used Cheese and it shows my cam, but the picture is in green (like it has a green effect) and it mirrored vertically.

in cheese I was able to fix the Vertically mirror  but the color is still in green .

I had the same problem in windows vista but for it I updated the new driver and it was fixed .

how I can fix it in ubuntu ?

(in skype it shows my picture vertically-mirrored and in green and I cant fix it there)

here is the result of lsusb for me

cheese identifies my webcams as sirius usb 2 camera /dev/video0

> 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ac8:3330 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a5c:2045 Broadcom Corp. Bluetooth Controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by Twitch6000 on 2009-11-03
Hum do you have any effects enabled through cheese?

What are your gstreamer settings?

---

### Post by medya on 2009-11-03
> **Twitch6000 said:**
> Hum do you have any effects enabled through cheese?

What are your gstreamer settings?

no I havent add any color effect using cheese and I told u it was like this in windows too (after I updated my driver)

and how do I know my gstreamer settings . (it is also mirrored-vertically)

---

### Post by Twitch6000 on 2009-11-03
Ah sorry I missed the part where you said it does this in windows aswell.

This leads me to believe that the driver could be the problem,or the webcam could be dying.

I would suggest reinstalling the driver on windows with the driver that was working.

If that fixes it,then it is a driver issue.

---

### Post by medya on 2009-11-03
it works fine in windows (after installing service pack), the problem is just in linux

---

### Post by medya on 2009-11-04
no more idea fellas?

---

### Post by think13 on 2009-11-04
Is there a way to change the hue settings in cheese? One thing I noticed after upgrading to 9.10 was that my colors were off for video. Changing the hue setting in Movie Player fixed that for me.

---

### Post by medya on 2009-11-04
there are color settings in cheese but it changes the color just in Cheese not in skype and it still wont be like normal color . I can change it to red or blue or gray

---

### Post by medya on 2009-11-04
is it possible to use Windows' driver for my webcam in linux ?

---

### Post by medya on 2009-11-06
any idea guys?

---

### Post by medya on 2009-11-10
official bump.

---

### Post by medya on 2009-11-12
crying :((

---

### Post by gja on 2009-11-22
I just solved the problem\ for my Trust webcam:
Check here:
[http://blog.export.be/2009/07/fixing-your-webcam-in-ubuntu-jaunty/](http://blog.export.be/2009/07/fixing-your-webcam-in-ubuntu-jaunty/)

---

### Post by gja on 2009-11-22
Better fix:

remove skype and install the skype version from medibuntu.

More info here:
[http://ubuntuforums.org/showthread.php?t=1306368&highlight=webcam+green&page=2](http://ubuntuforums.org/showthread.php?t=1306368&highlight=webcam+green&page=2)

---

### Post by medya on 2010-02-24
that link is not for me, it is for those who have their webcam in cheese but not in skype

I have cam everywhere but the problem is just it shows green and vertically mirrrored

---

### Post by no2498 on 2010-02-24
i have the same problem
colors are backwards 
green on the left red on the right as in not rgb
cam did start coming up facing  the right way
i did put in a few bug reports
but do not know how to give them all they need
its in the v4l1 to v4l2 some place
my cam opens in more programs than it ever did before can even get it open in flash but its just red point it at a light i can get pink
the only program i can change any thing in is cheese but it brakes every thing else

---

### Post by no2498 on 2010-02-25
open applications internet, ekiga softphone
an get the cam on try setting some settings it is changing mine a bit
hope this helps

---

