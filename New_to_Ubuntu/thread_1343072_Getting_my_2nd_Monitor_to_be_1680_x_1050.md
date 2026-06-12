---
title: "Getting my 2nd Monitor to be 1680 x 1050"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by jsievs on 2009-12-01
Hi,

I have recently begun to use Ubuntu for the first time and I REALLY like it.  One of the things I haven't been able to do yet is get my second, Samsung 23" monitor to display at the correct resolution.  

Under **System --->  Preferences   --->  Display**  I have successfully set up it up as 1280 x 1024 resolution.  However, this is the highest resolution that is listed in the drop down arrow for this monitor.

My question is:  How can I add the 1680 x 1024 resolution option so that my larger monitor will display at the correct resolution.    

My card is the Ati Raedon X200M Integrated. I downloaded what I thought was the correct video driver from the ubuntu software center.  However, when I click on it, (*Ati Catalyst Control Center)  *I get the following error message:[INDENT]*"There was a problem initializing Catalyst Control Center Linux edition. No Ati graphics driver is installed, or the ati driver is not functioning properly*.  *Please install the ati driver appropriate for your ati hardware*, [I]or configure using ati config.

[/I][/INDENT]I am a complete beginner so any help in layman's terms would be greatly appreciated.  After trying to search for help, I have seen that there might be a possiblity of editing the xorg.conf file, but mine only shows the info for 1 screen, even with the 2nd monitor up and running.  

I suppose this is a more advanced concern, but ultimately I would like to have true dual monitors.  Right now it is just one long monitor stretched across the 2 screens.  I can tell this because the desktop wallpaper is cut in half down the middle.  

Thanks for your help with these issues.

---

### Post by marco123 on 2009-12-01
Try installing the ATI drivers via System>Administration>HardwareDrivers.

---

### Post by LowSky on 2009-12-01
> **marco123 said:**
> Try installing the ATI drivers via System>Administration>HardwareDrivers.

Catalyst is a program that works with the driver, just so you know.

---

### Post by QIII on 2009-12-01
Unfortunately, I think ATI has discontinued support for your GPU and now considers it "legacy".  So you will not likely find an ATI driver for Linux that works with a recent version of Catalyst.

Unfortunately, some older versions of Catalyst, which would require the ATI driver anyway, do not work with the most recent version of X.

So you may be stuck with the open source driver, which may not give you the resolution you are looking for.

When I get home, I'll see if I can find more cheerful news.  You may be able to change your xorg configuration file, but I'll have to investigate.

---

### Post by QIII on 2009-12-02
The cheerful news:  Although xorg.conf does not exist by default in Karmic, you can create one.

Here's a discussion on the basic idea.

However, you may have to search the forums for how to set up xorg.conf to work with dual monitors.  (I'm not expert enough to offer advice.  I've always used the ATI and nVidia tools.)

[http://ubuntuforums.org/showthread.php?t=1325212](http://ubuntuforums.org/showthread.php?t=1325212)

---

