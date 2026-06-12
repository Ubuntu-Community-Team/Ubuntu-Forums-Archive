---
title: "stuck in an infinite loop"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by lam47 on 2008-12-15
Hey everyone.
I have only been using Linux for a week and love it already.
I do have one recurring issue that I dont seem to be able to fix.

As you can see from my xorg the mouse is causing this loop.
I dont understand what it means though.
I have been able to stop it by disabling the Nvidia drivers and using the non 3d accelerated ones.
However I would of course like to be able to have exposse and all the other graphical effects running too.

My system is,
AMD 6000+
8800 Ultra
Asus Crosshair
4GB ram
(have 2 mice connected currently, both do it individually too)

Im running 8.10 64 bit version. I have compiz installed for the effects.

If anyone can offer any advice I would be very grateful.

I am still at a stage where I need to be told the whole terminal commands though.
I will learn in time.


The loop message at the bottom of the xorg repeats for pages.

---

### Post by jbrown96 on 2008-12-15
I'm not really sure what's going on in the attached file. Do you have a liveCD that you boot from? Does the same problem happend? Are you able to reproduce it? You can always try to reconfigure the xserver with ```
sudo dpkg-reconfigure xorg-server
``` Unless you have some non-US keyboard, don't change any settings, just accept the defaults. Your Nvidia graphics card won't be using the proprietary drivers, so you will need to set them up again.

---

### Post by lam47 on 2008-12-15
I have tried the config and it boots OK no loop.
As soon as I enable the 177 drivers for the GPU I get the same loop.
No problems from a live CD as the drivers are not installed.
It makes no sense as other people are running them fine.

Thanks for the reply.

---

### Post by jbrown96 on 2008-12-15
Not sure what to tell you. You could try the new beta drivers from Nvidia. I'm using them, and they appear to run smoothly. However, installing Nvidia's drivers manually is pretty nasty, and I've never had much luck upgrading them. 

If you want to try, get the proper driver from [http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

Once downloaded, close out all your applications and press Crtl+Alt+F1. Login.
install some necessary files
```
sudo apt-get install build-essential kernel-source
```
stop the x server ```
sudo /etc/init.d/kdm stop
``` replace kdm with gdm if you are using gnome
install the driver
```
sudo sh ./Desktop/NVIDIA...
``` once you type NVIDIA you can press tab to complete the line. Follow the directions and restart when you are done.

---

### Post by lam47 on 2008-12-15
I will give them a go thanks man.

---

### Post by billgoldberg on 2008-12-15
It's seems like a bug in xserver-xorg-core or xserver-xorg-video-nv.

Downgrading those packages to an earlier version should work according to the debian bug report.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=462127](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=462127)

> 
I have decided to downgrade/revert to the version I had before
experiencing this bug, which is xserver-xorg-core 2:1.4.1~git20071119-1
2:1.4 and xserver-xorg-video-nv 1:2.1.6-1.


However that bug report is almost a year old, so it could be something completely different.

Go to launchpad an file a bug report.

---

### Post by jbrown96 on 2008-12-15
I forgot to say to choose the beta driver section. On the page where you fill out what card and system you have, don't select search. Below that there is a link to get beta drivers. The most current version, as of yesterday, is 180.116

---

### Post by billgoldberg on 2008-12-15
> **jbrown96 said:**
> I forgot to say to choose the beta driver section. On the page where you fill out what card and system you have, don't select search. Below that there is a link to get beta drivers. The most current version, as of yesterday, is 180.116

I don't think it's a good idea to advice new users on using beta drivers.

---

### Post by lam47 on 2008-12-15
well it all seemed to install correctly but now I just get this screen on boot.
[IMG]http://img.photobucket.com/albums/v331/laurie47/DSC00229-2.jpg[/IMG]

---

### Post by lam47 on 2008-12-15
Well I decided to try a fresh install and even a different distro.
I installed Opensuse which could not even recognize my mice.
It failed to do something on first startup, I could not see what exactly as it went so quick but there was a big red failed!
Not sure what to do now.

---

### Post by jbrown96 on 2008-12-16
Ouch, sorry you're having so much trouble. I tried an 8 series Nvidia (8800GTS) a few months ago and had lots of trouble with it. 

I did find a [thread]("http://ubuntuforums.org/showthread.php?t=965180") that might be of some use to you. It appears that editing your xorg.conf with the busid might help (comment #34), but the beta drivers could also be working (comment #36). 

I would recommend reinstalling and trying the busid method, but backup the xorg.conf file first. 
```
[CODE]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```[/CODE]
Then you can edit the file. 
If this method doesn't work (you should only need to Crtl+Alt+Backspace to check, undo the changes to you xorg. ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

I'm still leaning towards the beta drivers, though. Not sure exactly what happened last time. 
1) Make sure to remove the Nvidia driver that Ubuntu provides
2) Restart so the old driver isn't loaded
3) Have Nvidia automatically configure the xorg.conf file (last question in setup)
4) restart 
5) If you are dumped at the shell, login and try ```
startx
```

Best of luck

---

### Post by lam47 on 2008-12-17
Thanks man. I will be sure to give it a go.
I'm just unlucky I guess.
Currently just using vista but want to get Linux back!

---

### Post by lam47 on 2008-12-18
I did a fresh install of Ubuntu 64 bit today.
Also moved my hard drives around (physically to different sata ports)

And.

Well so far no problems. 177 Nvidia drivers not causing any issues at all.

---

