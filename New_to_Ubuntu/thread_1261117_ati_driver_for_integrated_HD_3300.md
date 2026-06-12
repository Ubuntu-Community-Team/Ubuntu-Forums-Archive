---
title: "ati driver for integrated HD 3300"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by carbon13 on 2009-09-08
I'm new to ubuntu and so far I'm loving it...except for some video driver problems:
 
I'm running 64-bit ubuntu 9.04 and I have an integrated Radeon HD3300 video card.
 
Here's the problem: the open-source driver (default on installation) works great for my HD movie playback but I can't use the 3D desktop effects from Compiz. When I install the proprietary fglrx driver, the 3D effects are great but my HD movie playback is all choppy and crashes often (on several different players). 
 
Is there any way to have both 3D desktop effects and smooth HD video playback??
 
-Carbon13

---

### Post by LowSky on 2009-09-08
Instructions for Ubuntu 9.04 (Jaunty)
from here
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Enable the accelerated ATI graphics driver in the 'Hardware Drivers' (System->Hardware drivers), then from terminal:
```

sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```

---

### Post by carbon13 on 2009-09-08
Thanks for the reply.

I activated the ATI driver through system>hardware drivers and then copied the dpkg command into the terminal. Everything was OK up to there. When I copied the insmod command line into the terminal, I got the following error:

insmod: can't read '/lib/modules/2.6.28-15-generic/volatile/fglrx.ko': No such file or directory

My HD video playback is still choppy but at least catalyst is recognizing my display now (for the 1st time).

Any thoughts on how to fix the video playback?

As an aside - I did a fresh ubuntu 9.04 install and this is essentially the first thing I'm doing before any other software install or restricted extras.

-Carbon13

---

### Post by 3rdalbum on 2009-09-08
Try changing the video output module in your video player. If it's set to "XVideo", then change it to "X11". Or vice-versa. ATI's driver supports video decoding acceleration but they have not released specifications or code to the developers of video playing programs, so nobody can take advantage of it yet!

---

### Post by Excedio on 2009-09-08
I had that problem also. I was able to remedy it by going to System > Preferences > Multimedia Systems Selector

Click on the Video tab and set the output plugin to X Window System (No Xv). If that does not work, you can always try upgrading your video driver to the latest, if you have not already. That fixed a lot of problems I was having.

---

### Post by Excedio on 2009-09-09
Here is a link to the latest drivers if you want them.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

---

### Post by QIII on 2009-09-09
Try switching to Metacity while running your video app and see how that goes.

If that works, you may have to switch back and forth -- Metacity when watching video media, Compiz the rest of the time.

---

### Post by carbon13 on 2009-09-10
> **Excedio said:**
> I had that problem also. I was able to remedy it by going to System > Preferences > Multimedia Systems Selector

Click on the Video tab and set the output plugin to X Window System (No Xv). If that does not work, you can always try upgrading your video driver to the latest, if you have not already. That fixed a lot of problems I was having.
Thanks for the replies.
 
I was able to get it working with the 
 
System > Preferences > Multimedia Systems Selector

Click on the Video tab and set the output plugin to X Window System (No Xv). 
 
One clarification for newbees like me, you have to do this first:
 
System > Preferences > Main Menu
 
Enable the Multimedia Systems Selector checkbox
 
Thanks again to everyone that responded!!
 
-Carbon13
[FONT=Georgia][SIZE=1][FONT=Georgia][SIZE=1][/SIZE][/FONT][/SIZE][/FONT] 
[FONT=Georgia][SIZE=1][FONT=Georgia][SIZE=1] 
[/SIZE][/FONT][/SIZE][/FONT]

---

