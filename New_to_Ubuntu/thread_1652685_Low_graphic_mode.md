---
title: "Low graphic mode"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by maksim_m on 2010-12-25
I've installed Linux and began to install dbus,glib,expat,bluez....according to README file (./configure then make && make install) and it is gone well.I could compile and run my bluetooth application.But after rebooting, my desktop doesn't boot up and pops up the follow message: 
"Ubuntu is running in low graphics mode.The screen,graphics card and input devise setting are not detecting properly.You should reconfigure those by yourself "
 
I run ubuntu 10.10.I tried 'nomodeset" and another option from grub it is not helpfull.
What could I try to fix it?

---

### Post by cariboo on 2010-12-25
FIrst off, why are you installing from source, instead of just installing packages from the repositories. Check the Software Center or System->Administration->Synaptic Package Manager.

To solve your graphics problem, you'll have to let us know what graphics chipset your system is using.

---

### Post by maksim_m on 2010-12-26
My graphics card is ATI Radeon HD 3200. But it is strange that it worked well before mentioned packet installation.

---

### Post by maksim_m on 2010-12-28
I checked up Software Repository as were suggested, and it seems that bluez,dbus,glib are exsisting.But while compiling my application it asks for addition libraries therefore I was forced to install bluez package and it requires D-Bus library.And after rebooting I get the same problem!

---

### Post by cariboo on 2010-12-28
What graphics driver are you using? how did you install it?

---

### Post by maksim_m on 2010-12-28
It uses ubuntu's driver.I have not installed additional graphics card driver.In one of attempts I tried to install suggested(by ubuntu hardware utility )updated driver for ATI and it got me to the same problem even before dbus and glib installation.

---

### Post by cariboo on 2010-12-28
You should try and install the recommended driver when you go to System->Administration->Hardware Drivers. It should install all the dependencies needed without having to install any extras.

I would also suggest you create a backup of /etc/X11/xorg.conf if you have one eg:

```
sudo mv /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
```

And reboot, you start up using the open source driver which should give you at least 1024X678 resolution.

I would suggest you stick with installing from the repositories, as almost everything you need can be installed using either the Software Center, or Synaptic Package Manager.

---

### Post by maksim_m on 2010-12-29
Thanks for reply.
But again,I have some application that uses bluez-libs and bluez-utils.Checking up Ubuntu's software Center it looks that all mentioned above packages exsist but my app doesn't pass compilation and asks install more.Searching for particular pakchages it looks that they are installed. For instance typing:" apt-get install dbus" says me that I have lastest version,but while compilation it it says that I need D-BUS library,same with 'expat'. I''ll try install suggested ATI driver again.
Sorry,may be there is some kind of misunderstanding.

---

### Post by maksim_m on 2010-12-29
how can I install dbus-glib binding using Software Center?

---

### Post by cariboo on 2010-12-29
Have you tried libdbus-glib-1-2?

Are we trying to solve two different problems at the same time?

---

### Post by maksim_m on 2010-12-29
No,I just try to figure out how to install particular package using Software Center.Because, typing the name of desired package in searching area I get the list of packages and no way to understand what they are.Majority of packages that I have, were taken  from different sources,now I try to get them from repository, using Software Center.

---

### Post by SunnyRabbiera on 2010-12-29
For basic stuff usesubuntu software center, but if you need more packages use synaptic, its the same thing just no icons for the packages.
I just had an issue with my graphics card and the est solution is to go into recovery mode, load the safe graphics option, and uninstall/reinstall your graphics card driver.

---

### Post by cariboo on 2010-12-29
Is the blue application in the repositories? Or did you create it yourself?

---

### Post by maksim_m on 2010-12-30
I've created bluetooth application ,using BlueZ, that including libraries and utilities.Bluez(bluetooth stack) package was taken from  [www.bluez.org]("http://www.bluez.org") and while installation it asks for some more packages(dbus library,glib,expat...) that I got from google......now I try to get these packages from Software Center. My last attempt got me know that after dbus installation .....I got the problem

---

### Post by maksim_m on 2010-12-30
Thank you very much for assistance.The issue is solved.I worked around as follow:
I installed updated ATI driver,suggested by ubuntu then I installed bluez,dbus,glib.....packages from repositories, using Synaptic, as were suggested here.I managed to run my bluetooth application and to reboot my system !!!

---

