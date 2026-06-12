---
title: "Is there a way to skip this boot screen and what are the differences?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by ni ni on 2009-03-21
hello all!

is there a way to skip the following boot screen, and what on earth is the difference between 27-11 and 27-7??????????

ubuntu 8.10, kernel 2.6.27-11-generic
ubuntu 8.10, kernel 2.6.27-11-generic (recovery)
ubuntu 8.10, kernel 2.6.27-7-generic
ubuntu 8.10, kernel 2.6.27-7-generic (recovery)
ubuntu 8.10, memtest86+


thank you  x x x x x xx

---

### Post by SunnyRabbiera on 2009-03-21
There is usually more then one kernel listed as a precaution, often times an older kernel might work better then a new one.
If one works use it, the other doesnt take up any real room.

---

### Post by drs305 on 2009-03-21
ni ni,

I wrote a guide about startup-manager, a gui app that helps edit menu.lst options. It discusses why you see multiple kernel options, how to limit them if desired, and how to remove them from either the menu and/or your system. Startup-Manager also allows you to tweak many other menu options, such as setting the default kernel, whether or not you want to see the menu at all, and for how long. 

All these options are available by manually editing menu.list but startup-manager can do it for you without having to open the file and edit it yourself. 

The link to the guide is in my signature line.

---

### Post by presence1960 on 2009-03-21
> **ni ni said:**
> hello all!

is there a way to skip the following boot screen, and what on earth is the difference between 27-11 and 27-7??????????

ubuntu 8.10, kernel 2.6.27-11-generic
ubuntu 8.10, kernel 2.6.27-11-generic (recovery)
ubuntu 8.10, kernel 2.6.27-7-generic
ubuntu 8.10, kernel 2.6.27-7-generic (recovery)
ubuntu 8.10, memtest86+


thank you  x x x x x xx

Those are the 2 most recent kernels you have. You might want to leave 2 kernels in there in case one becomes unbootable or non-functional for whatever reason. 

+1 on drs305 reply start up manager works well. To install use synaptic or in terminal :  > sudo apt-get install startupmanager

---

### Post by ivanvajar on 2009-03-21
Why would you skip boot screen? If you don't want to look at it for a long time, it would be better if you shorten dispaying time of that screen to 2s.

---

### Post by ivanvajar on 2009-03-21
Open Terminal and run:

> sudo gedit /boot/grub/menu.lst

Find the line that says **_[U]timeout_[/U]** and enter new time (2 seconds at least)

---

### Post by rburkartjo on 2009-03-21
i have my boot screen set for 10second display and have at least the previous kernnel shown. you never know when you have problems. evenwith a 10 second display if you hit enter it will kill the display and go thru the start process.

---

### Post by Kevbert on 2009-03-21
> **ivanvajar said:**
> Open Terminal and run:
sudo gedit /boot/grub/menu.lst 
Find the line that says **_[U]timeout_[/U]** and enter new time (2 seconds at least)

Set timeout to 5 (seconds) and uncomment #hiddenmenu so it reads
```
hiddenmenu
```
then if you want to see the menu just hit Esc when prompted.

---

### Post by ivanvajar on 2009-03-21
Yup! That's nice option too :-)

---

