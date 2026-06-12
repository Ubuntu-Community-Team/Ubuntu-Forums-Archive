---
title: "Having problems with Ubuntu"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by scythe01 on 2009-04-25
I just had a new desktop with trial version of windows xp but it suddenly asked me for activiation and I couldn't logged-in. So I installed Ubuntu 8.04 LTS using a cd I got from a dormmate.

I am having lots of problem since I am only new to Ubuntu. 
*It only allows to adjust the resolution of my lcd monitor up to 800x600, not to its optimum resolution of 1440x900.
*I can't find the windows when I minimize them.
*My video card seems not to be working. It is a nvidia gforce 9300gs
*I can't watch videos
*can't run .exe files


Sorry, I am a total noob....:(

Thanks  guys

---

### Post by lisati on 2009-04-25
You might want to check out a newer version. You can download a copy [here]("http://www.ubuntu.com/getubuntu/download"), or order a free CD [here]("https://shipit.ubuntu.com/")

As for running EXE file, they don't normally work with Ubuntu without help because they're designed for Windows: have a look here: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by Ocxic on 2009-04-25
use the restricted drivers manager in the admin menu to install the proper driver for you video card.
in add/remove install ubuntu-restriced-extras, and all of the gstreamer plugins for video.
and .exe will not work in ubuntu, you'll need to install wine, and good luck.

---

### Post by saidinesh5 on 2009-04-25
first and foremost you have an NVIDIA card , so lets get it running :
you need to download and install the drivers for your NVIDIA card. 

->you can do that manually by downloading the drivers from NVIDIA website 
          OR 
-> go to system>Administration-> restricted drivers and simply enable the recommended drivers for your graphics card.
---after this installation and a restart, your display related problems will get solved.

in order to watch your videos, you need to download and install the approp. codecs. 

linuxondesktop.blogspot.com 
visit this website to get more info. on how to customize your ubuntu to do these tiny little tasks.

and now for the .exe files, they are WINDOWS' files : so they dont natively run on linux. but you can run them using softwares like WINE / Crossover.

hope your problems are solved. :)

---

### Post by scythe01 on 2009-04-25
*The Hardware Driver said that "No proprietary drivers are in use in the system". 
*How to install the downloaded driver from NVIDIA.
*Why can't I see where the minimized windows goes?

Thanks for the help guys

---

### Post by jmszr on 2009-04-25
scythe01,

       This thread should deal with your driver issue: [http://ubuntuforums.org/showthread.php?t=819146](http://ubuntuforums.org/showthread.php?t=819146) . Start with iaculallads' advice in the 4th post in this thread and then go to the guide.  Also to open your terminal: Applications > Accessories > Terminal. Remember: copy & paste and Google are your friends.

---

### Post by NightwishFan on 2009-04-25
The minimized windows go to the same place, the bottom panel. If there is no bottom panel then it was removed, so right click the bottom panel, and choose add to panel, and search for button. There should be something yada yada button and add that there ya go. It is pretty similar to windows, only easier. Unless you randomly remove panel applets, which can get frustrating to restore to default.

If you have a nvidia card, it should appear in the restricted drivers. If not, reboot and try again. If not then you have a rare card or it is not nvidia. I have an old 6 series and it works fine. If you are sure it is nvidia and it does not appear in the restricted drivers list, then please inform us.

Any other specific issues please post.

---

### Post by scythe01 on 2009-04-25
I'm sure it's nvidia, a gforce 9300gs. I already rebooted for a lot of times but there are still nothing in the Hardware Drivers' list.

---

### Post by tekkieguy on 2009-04-25
Wait???
You're using 8.04!?!?!?!?!?!?!?
Well download 9.04, that should fix a lot of things.
[http://ubuntu.com](http://ubuntu.com)

---

### Post by scythe01 on 2009-04-25
I already tried to burn the iso file into cd twice. Both have I/O problems. Is it because I used 9.4x, it is the lowest possible speed for my writer.

---

### Post by tekkieguy on 2009-04-25
Well i never use the CD....
I always use Ubuntu's start up disk creator to my USB drive if im on Ubuntu
[system>admin]
or i use Unetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
When im on a Windows system, or Ubuntu's isnt working. 
When I use my USB stick, install is done in 10min.

---

### Post by scythe01 on 2009-04-25
Can you to tell me the steps in installing using a USB stick?

---

### Post by tekkieguy on 2009-04-25
> **scythe01 said:**
> Can you to tell me the steps in installing using a USB stick?
Sure!!!!
I am assuming that you are running Ubuntu so....
Go to system>administration>usb start-up disk creator.
And then click other, and then  click where the ISO is, and then select what USB disk you want it installed on. [you need a minimal 1gb for ubuntu desktop].

---

### Post by scythe01 on 2009-04-25
Thanks, I'll give it a try. I hope my problems will be resolved after I installed the new version.

---

