---
title: "Cannot login to Ubuntu 9.10"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by HINDYhat on 2009-11-30
I finally gave up on Windows and I decided to install Ubuntu (9.10 64 bit). After many tries of configuring my wireless connection, I've finally succeeded that. And so I thought that my problems were over.

Ubuntu was working great at first. Wireless was flawless, incredibly fast, super easy to use. I tried to enable desktop effects, and it didn't let me. I'm running on an nVidia 9800gtx+, and Ubuntu said that I required some special drivers. After attempting to download them, I received some error message (which I can't remember), so I tried again and it didn't work. I then rebooted my computer.

Ubuntu reached the login screen as usual. Unfortunately, though, I was unable to login. It seemed as if my password wasn't accepted: when I enter my password and login, the screen flashes once or twice, and then goes back to the login screen with a little bongo sound effect. After mindlessly bashing my keyboard, I realized that Ctrl+Alt+F1 would bring me to a command line. From there, I was able to login fine. Not able to actually do anything, though, since it's just a command line and I'm just an Ubuntu newb. I've also read that there are issues with nVidia drivers on 9.10. Should I just install 9.04 and get rid of this issue, or is there a simple way to fix it on 9.10?

Also, I read about some flickering issue with faulty nVidia drivers or something of the like. The screen doesn't actually flicker constantly, it looks fine. That's not my issue.

---

### Post by mbzn on 2009-11-30
It is possible to boot without the nvidia drivers(not sure about how in 9.10). Try to disable them first so you can boot into your GUI. from there it will be a little easier to try and solve your problem.

---

### Post by RochJer on 2009-11-30
To fix some unusual issue with the nVidia graphic card, I would recommend you to look into Restricted Drivers with nVidia - usually the recommended version for nVidia is 185. Try to upgrade this nVidia card with this Restricted Driver then you should be prompted to reboot ubuntu then try again.

---

### Post by pbrane on 2009-11-30
It's not that the nVidia drivers are faulty. I use the nVidia drivers just fine. Try having a look at this:
[http://ubuntuforums.org/showthread.php?t=1125400]("http://ubuntuforums.org/showthread.php?t=1125400")

I know it is for the 185 drivers but I used this to install the latest 190.42 nVidia drivers.

Also try typing **sudo dpkg-reconfigure -phigh xserver-xorg** to reset your xorg config back to default for your system.

---

### Post by efflandt on 2009-11-30
While not familiar with nVidia issues, I did have problems with an old ATI card that was not supported by current default drivers.  At the bottom of the login screen where it says **GNOME** is actually a dropdown list.  Try logging into **Failsafe GNOME**.  While some things you can do there are limited (hopefully you already working network connection), it should put you on more familiar ground where you can use a web browser, add/remove packages, etc.  That allowed me to add the package I needed for the old ATI video.

Although, you may need to figure out how to clear out whatever you tried to install (maybe it was for an older version of X).

---

### Post by HINDYhat on 2009-12-01
I'll be sure to refer to this if I ever have problems with 9.04. I decided to remove 9.10 and install 9.04 instead, based on advice given by a friend (he said that 9.10 was full of bugs and isn't worth the upgrade).

Thanks anyway!

---

