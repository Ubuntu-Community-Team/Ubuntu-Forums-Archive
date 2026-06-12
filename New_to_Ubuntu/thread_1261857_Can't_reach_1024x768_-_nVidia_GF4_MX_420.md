---
title: "Can't reach 1024x768 - nVidia GF4 MX 420"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Seanj72 on 2009-09-09
Hi, I am very new to Linux and this is my first Ubuntu install.  I'm hoping someone can help me with an annoying situation...  After initial install, I'm left in 800x600 and when I try and change this via System -> Preferences -> Display, my monitor is labelled as 'Unknown' and 'Detect Monitors' does nothing.  Not even a flicker.  My Max Resolution in the dropdown is 800x600.  (of course i'd like to get to at least 1024x768)
 
So... Then after much tinkering i realized that going to System, Administration, Hardware Drivers, the system would auto download and give me the option of installing and using nVidia accelerated graphics driver (version 96) 'Tested by the Ubuntu developers'  Sounds great!  I thought this was the 'missing link'.  Unfortunately did not help.  In fact, after I let the system load this graphics driver, then i'm stuck in 640x480 max!  Then it's almost totally impossible to navigate anywhere to do anything in terms of troubleshooting.  Can't seem to get the nVidia panel to change anything for me in terms of video config settings.  Seems this has something to do with the fact the OS can't properly detect my screen for some reason.  I have a Citizen 15" LCD that is capable of 1024x768. (i have it in 1024x768 on my Windows OS)  The system is a Dell desktop with an nVidia GeForce4 MX420 video adapter.  Help!

---

### Post by wojox on 2009-09-09
Open your terminal and:

```
gksudo nvidia-settings
```

Edit from there.

---

### Post by Seanj72 on 2009-09-09
That brings up the nVidia GUI which seems to be useless in this situation.  Can't change anything.  Under X Server Display Configuration, My Display is listed as CRT-0 (CRT-0 on GPU-0) and the resolution dropdown has:  Auto (current setting), 640x480 and 320x240 (oh joy).  The 'Detect Displays' button makes the screen flicker but then does nothing and no menu item choices change.  Do I possibly need to try and force some settings via the conf file?  If so, what settings and how?
 
I was thinking of trying this (Installing different nVidia drivers)
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by Seanj72 on 2009-09-09
Still not getting anywhere with this...  I don't think Ubuntu likes my video configuration...

---

### Post by wojox on 2009-09-09
You could try to force it:

```
gksudo gedit /etc/X11/xorg.conf
```

Scroll down to Screen Options

---

### Post by Seanj72 on 2009-09-09
I ended up loading/forcing a driver package from nVidia's website.  The install went well, but now after initial bootup, I get the Ubuntu logo, then screen goes black and I loose signal and I get the 'Out of Range' message from my monitor.  I've been editing the xorg.conf file and I keep on raising the refresh rate, but still same issue.
 
For the screen resolutions, there is just a line that shows some choices, but it's unclear in the conf file which one it is currently set on.

---

### Post by LowSky on 2009-09-09
boot into recovery mode and choose xfix, it will reset your xorg file

---

### Post by Seanj72 on 2009-09-09
Right... but now i'm trying to figure out how to force the settings in xorg.conf to 1024x768 at a safe refresh rate like 60Hz

---

### Post by Caddy2187 on 2009-09-09
I am also very new to Ubuntu, I installed it a few days ago and had the exact same problem. in System -> Administration -> Hardware drivers is the nVidia version 180 availible, this is what resolved my problem.

P.s, sorry if I'm no use, I'm completely new but thought I'd share since I had the same problem

---

### Post by NightwishFan on 2009-09-09
You can try a different or newer Nvidia driver. These other guys will help you out.

---

### Post by Seanj72 on 2009-09-09
Thanks for your input anyway, no just the version 96 is available in the hardware Drivers dialog... which doesn't seem to like my config.
 
I'm still trying to manually manipulate the xorg.conf to try and force 1024x768, but no deal so far.

---

### Post by NightwishFan on 2009-09-09
That sounds like a messy solutions. I will try to google your card and search for compatibility issues.

---

### Post by wojox on 2009-09-09
I went to the nvidia website and checked as well and it said version 96 was the only one for your card. I think it may be time for a card upgrade. Or sit real close to the monitor. :lolflag:

---

### Post by Bölvaður on 2009-09-09
I try to avoid installing the drivers from the website so if you are able to find this driver in .deb format then rather go for that one, or is in a PPA

[http://www.nvidia.com/object/linux_display_ia32_96.43.13.html]("http://www.nvidia.com/object/linux_display_ia32_96.43.13.html")


It looks like the same driver as you already had so perhaps there was a mixup with a config file, like perhaps xorg.conf

after installing you can check if you are using the VESA (kind of like a default driver) or a nvidia one, by opening the terminal (applications &#8594; accessories &#8594; terminal)
```
glxinfo
```
or the same command with a filter
```
glxinfo | grep client
```

the difference between having a correct driver and incorrect can be detected by a quick test with
```
glxgears
```
wrong driver should give you less than 500 fps, and the correct one above 1000 fps (probably few times higher than that)

---

### Post by NightwishFan on 2009-09-09
Try doing the xfix in recovery mode and then reinstalling the Nvidia 96 driver.

If you cannot get the deb driver working you can always compile the Nvidia one. I do not recommend it though.

32-bit Linux:
[http://us.download.nvidia.com/XFree86/Linux-x86/96.43.13/NVIDIA-Linux-x86-96.43.13-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.13/NVIDIA-Linux-x86-96.43.13-pkg1.run)

---

### Post by Seanj72 on 2009-09-09
> **Bölvaður said:**
> I try to avoid installing the drivers from the website so if you are able to find this driver in .deb format then rather go for that one, or is in a PPA
 
[http://www.nvidia.com/object/linux_display_ia32_96.43.13.html](http://www.nvidia.com/object/linux_display_ia32_96.43.13.html)
 
 
It looks like the same driver as you already had so perhaps there was a mixup with a config file, like perhaps xorg.conf
 
after installing you can check if you are using the VESA (kind of like a default driver) or a nvidia one, by opening the terminal (applications &#8594; accessories &#8594; terminal)
```
glxinfo
```
or the same command with a filter
```
glxinfo | grep client
```
 
the difference between having a correct driver and incorrect can be detected by a quick test with
```
glxgears
```
wrong driver should give you less than 500 fps, and the correct one above 1000 fps (probably few times higher than that)
 
By manually editing the xorg.conf file and using settings based on researching my screen specs, I was able to get the screen working at 1024x768 and above!  In fact when it finally came to life, it was at a resoltion of 1300xSomething.  Monitor is not even supposed to support that!  Anyway, I am now in 1024x768 @ 60Hz and all is good, although it's unlcear what driver i'm using now, so I will try the above tests by Bölvaður and see how it goes!  Thanks for everyones help on this!

---

### Post by NightwishFan on 2009-09-09
Excellent, glad you got it working. I am surprised that you can get a higher resolution. I would be careful if your monitor does not support it though.

---

