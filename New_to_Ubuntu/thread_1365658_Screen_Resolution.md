---
title: "Screen Resolution"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by GLSmyth on 2009-12-27
I am trying to move from Windows to Linux and am running into a problem with my screen resolution.  I installed the latest version on my Toshiba Portage and it looks like I am stuck at an 800x600 resolution.  I was told that this could be a bug so I tried an older version ([http://releases.ubuntu.com/hardy/ubuntu-8.04.3-desktop-i386.iso](http://releases.ubuntu.com/hardy/ubuntu-8.04.3-desktop-i386.iso)) and am still having the same problem.

Is this something that just doesn't work, or can it be fixed?  Obviously, I'll have to switch back to Windows if I cannot get to the 1024x768 resolution my screen will allow.

Thanks -

george

---

### Post by the.dark.lord on 2009-12-27
What exactly happens when you try to change the resolution?

---

### Post by Cheesemill on 2009-12-27
Have you installed the drivers for your graphics card?

Go to System > Administration > Hardware Drivers and see if there is anything available for installation.

---

### Post by kansasnoob on 2009-12-27
Could you please list the specific Toshiba model info?

---

### Post by GLSmyth on 2009-12-27
> **the.dark.lord said:**
> What exactly happens when you try to change the resolution?

800x600 is the highest resolution offered to me.

Cheers -

george

---

### Post by GLSmyth on 2009-12-27
> **Cheesemill said:**
> Have you installed the drivers for your graphics card?

Go to System > Administration > Hardware Drivers and see if there is anything available for installation.

Doing this offers me the response, "No proprietary drivers are in use on this system."

Cheers -

george

---

### Post by Chris Edgell on 2009-12-27
[http://ubuntuforums.org/showthread.php?p=7299623#post7299623](http://ubuntuforums.org/showthread.php?p=7299623#post7299623)

Read this post, see if it pertains to you.

Best of luck!

---

### Post by GLSmyth on 2009-12-27
> **kansasnoob said:**
> Could you please list the specific Toshiba model info?

Toshiba Portege R100
1. 0PM/12X/512/40/W (not sure what that means, but is below the system description under the label on the bottom)
Part No. PPR10U-05N217

Cheers -

george

---

### Post by the.dark.lord on 2009-12-27
Also see this:

[http://ubuntuforums.org/showthread.php?t=1346500](http://ubuntuforums.org/showthread.php?t=1346500)

---

### Post by GLSmyth on 2009-12-27
> **Chris Edgell said:**
> [http://ubuntuforums.org/showthread.php?p=7299623#post7299623](http://ubuntuforums.org/showthread.php?p=7299623#post7299623)

Read this post, see if it pertains to you.

Best of luck!

Thanks for the info.  I found the xorg.conf file but am not exactly sure what to do.  Should I just add "Defaultdepth 16" after the last "EndSection?"  Do I reboot after making the change?  I am guessing that this is a file that is read during boot.

Cheers -

george

---

### Post by GLSmyth on 2009-12-27
> **the.dark.lord said:**
> Also see this:

[http://ubuntuforums.org/showthread.php?t=1346500](http://ubuntuforums.org/showthread.php?t=1346500)

 cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

Cheers -

george

---

### Post by kansasnoob on 2009-12-27
This is written for Kubuntu but should be helpful (especially pay attention to step #6):

[http://www.kubuntu-portege.blogspot.com/](http://www.kubuntu-portege.blogspot.com/)

I always look here when messing with a Toshiba:

[http://www.linux-on-laptops.com/toshiba.html](http://www.linux-on-laptops.com/toshiba.html)

---

### Post by Chris Edgell on 2009-12-27
This is MY problem, I can point to something I've read...but someone else will have to read that post and see if they can answer your questions about it.

Heres hoping!  In fact, I've probably shed some light on what's wrong with this approach I've taken.  It is basically showing how someone else solved their problem.  It may not pertain so much to your problem.

---

### Post by GLSmyth on 2009-12-27
> **kansasnoob said:**
> This is written for Kubuntu but should be helpful (especially pay attention to step #6):

[http://www.kubuntu-portege.blogspot.com/](http://www.kubuntu-portege.blogspot.com/)

I always look here when messing with a Toshiba:

[http://www.linux-on-laptops.com/toshiba.html](http://www.linux-on-laptops.com/toshiba.html)

Apparently Configure X is the solution, according to that message, but I don't know what Configure X is or what to do with it (remember, I'm coming from Windows).

Cheers -

george

---

### Post by Chris Edgell on 2009-12-27
Gee, here I am again saying go read this thread:
[http://ubuntuforums.org/showthread.php?t=1158177](http://ubuntuforums.org/showthread.php?t=1158177)

---

### Post by GLSmyth on 2009-12-27
> **Chris Edgell said:**
> [http://ubuntuforums.org/showthread.php?p=7299623#post7299623](http://ubuntuforums.org/showthread.php?p=7299623#post7299623)

Read this post, see if it pertains to you.

Best of luck!

I think that I found the values that I am supposed to enter into xorg.conf but unfortunately the system will not allow me to save the file.

Cheers -

george

---

### Post by lotharmat on 2009-12-27
you need to open it as follows

```
gksudo gedit /etc/X11/xorg.conf
```

This opens the file with the necessary privileges to edit it.

---

### Post by GLSmyth on 2009-12-27
> **lotharmat said:**
> you need to open it as follows

```
gksudo gedit /etc/X11/xorg.conf
```

This opens the file with the necessary privileges to edit it.

Thanks for the info.  I am now using the full screen, but am still stuck in the 800x640 resolution.

Cheers -

george

---

### Post by lotharmat on 2009-12-27
does your xorg.conf contain this?

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
SubSection "Display"
Depth 24
Modes "1024x768@60" 800x600@60" "800x600@60" "640x480@60"
EndSubSection
EndSection

---

### Post by GLSmyth on 2009-12-28
> **lotharmat said:**
> does your xorg.conf contain this?

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
SubSection "Display"
Depth 24
Modes "1024x768@60" 800x600@60" "800x600@60" "640x480@60"
EndSubSection
EndSection

I tried a similar modification yesterday and when I restarted the screen was scrambled.  I have reinstalled everything and added information to the Display section and now for some reason I have 1024x768.  I have no idea why this is the case, but am just glad that I now have something I can use.

Cheers -

george

---

### Post by sujan01 on 2009-12-28
I am having similar problem with my old 18# Sony 420GS monitor.  It appears that the Ubuntu 9.10 boot loader (GRUB 2) does not detect some monitors even though the driver is available.  For example, after initial boot when I look at System->Preferences->Display, it shows "unknown" monitor.  The highest resolution for the unknown monitor is 800x600.  Then I put the monitor power off and then on again.   This time when I look at System->Preferences->Display, it shows "SONY 18"".  Then I can set the resolution at 1024x768 or one of many other choices going up to 2048x1536.  Will someone investigate why GRUB 2 does not detect the monitor while power on/off detects it?

---

