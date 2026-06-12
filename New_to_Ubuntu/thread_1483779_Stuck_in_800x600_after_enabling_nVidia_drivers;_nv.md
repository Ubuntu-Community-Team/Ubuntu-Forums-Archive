---
title: "Stuck in 800x600 after enabling nVidia drivers; nvidia-settings doesn't work either"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by diablo75 on 2010-05-15
I just built a new system for someone recently who is new to Ubuntu and is absolutely in love with it.  Unfortunately, we're having problems with the nVidia drivers...

So here's the skinny:

He's got a nVidia GeForce GT 240 PCI-Express adapter with 1GB of VRAM.

This video card worked fine when I tried it out, with one little hiccup when switching from HDMI output back to DVI (tested it on a TV, then took it back to a standard LCD monitor).  When I did this, I got the standard "Ubuntu is running in Low Graphics mode" prompt during boot... and I don't exactly remember what I did to get it fixed...

Anyway, he has the system at his place now and I'm trying to diagnose it by remote.  His drivers are enabled (as they were when I sent them) and the last display that it was attached to was a 19-in LCD via an SVGA cable.  He is now attaching it to a 27-inch 1080p monitor using a DVI to DVI cable.

The video works perfectly (resolution wise) when the nVidia drivers are *disabled*.  But if I enable them (by the way, the Hardware Drivers Manager does not say what version the drivers are, but only offers one choice and says in parentheses "(current version)" next to it) and restart the computer, resolution drops to 800x600.

The first thing we checked was System>Preferences>Monitors.  That produces the following error message:

> It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

If I click NO, and proceed, I can't pick a resolution higher that 800x600...

If I click YES to this question, it tries to start the nvidia-settings control panel which produces it's own error message:

> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.

And if I run "sudo nvidia-xconfig" like it suggests, it says a new configuration has been written to the xorg.conf file and to restart X.  So we restart and get the "Ubuntu is running in Low Graphics mode" error during boot.  We tried to select "Reconfigure graphics" which says it has created a new configuration and backed up the current config and to restart after that.  We then click Cancel to revert to the previous menu and select "Start with Defaults" (something like that) which we just assumed would be the newly generated configuration... but it just ends up being 800x600 all over again.

I'm not exactly sure what to do about this or the best way to fix it.  For the time being he is running with the drivers disabled so he can at least enjoy Ubuntu at the magnificent resolution of 1920x1080.  We would like to get this fixed so he can start playing with Compiz (a HUGE selling point for him).

---

### Post by Ozymandias_117 on 2010-05-15
Is it possible that his kernel was updated and new modules weren't made?

Have you tried disabling the drivers in jockey then reinstalling them?

---

### Post by diablo75 on 2010-05-15
> **Ozymandias_117 said:**
> Have you tried disabling the drivers in jockey then reinstalling them?

Yup, disabled the drivers, rebooted, things looked much better, re-enabled the drivers, things went back to the dark ages in terms of screen resolution (800x600).

---

### Post by Ozymandias_117 on 2010-05-15
Have you tried getting the newest proprietary drivers from nvidia's site? It really sounds to me like for whatever reason the kernel modules aren't there.

---

### Post by Sealbhach on 2010-05-15
Maybe you could try this driver?

[http://www.nvidia.com/object/linux-display-amd64-195.36.24.html](http://www.nvidia.com/object/linux-display-amd64-195.36.24.html)

The one in the ubuntu repos is 195.36.15, so not the latest one.

Also, have a look at thread here on installing Nvidia drivers manually,

[http://newyork.ubuntuforums.org/showthread.php?p=9300761](http://newyork.ubuntuforums.org/showthread.php?p=9300761)

 you probably only need to look at it if you run into trouble.

.

---

### Post by diablo75 on 2010-05-15
> **Sealbhach said:**
> Maybe you could try this driver?

[http://www.nvidia.com/object/linux-display-amd64-195.36.24.html](http://www.nvidia.com/object/linux-display-amd64-195.36.24.html)

The one in the ubuntu repos is 195.36.15, so not the latest one.

Also, have a look at thread here on installing Nvidia drivers manually,

[http://newyork.ubuntuforums.org/showthread.php?p=9300761](http://newyork.ubuntuforums.org/showthread.php?p=9300761)

 you probably only need to look at it if you run into trouble.

Just curious:

If I install this driver, will it appear within Jocky/Hardware Drivers Manager and allow me to disable it from there if things don't work?

---

### Post by lkraemer on 2010-05-15
This might be of help:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Also:
[http://ubuntuforums.org/showthread.php?t=1474284](http://ubuntuforums.org/showthread.php?t=1474284)

lk

---

### Post by Sealbhach on 2010-05-15
> **diablo75 said:**
> Just curious:

If I install this driver, will it appear within Jocky/Hardware Drivers Manager and allow me to disable it from there if things don't work?

No. It's from outside the normal software channels. 

If you want to uninstall it, have a look [here]("http://us.download.nvidia.com/XFree86/Linux-x86/195.36.24/README/installdriver.html").

Basically, the installer install the nvidia-installer utility to 

 /usr/bin/nvidia-installer

If you want to later uninstall the driver and undo what you've done, the command would be:

```
sudo /usr/bin/nvidia-installer --uninstall
 
```You may have to cd there and run it like this:

```

./nvidia-installer --uninstall
```.

---

### Post by -humanaut- on 2010-05-15
What driver are you using "current" ?

---

### Post by diablo75 on 2010-05-16
> **-humanaut- said:**
> What driver are you using "current" ?

Like I said, I have no idea.  This is litterally what it displayed itself as in jockey.  I'm about to try installing the newer driver manually.  (Crossing fingers)...

---

### Post by sailor2001 on 2010-05-16
in synaptics (system/admin) search and download "start-up  manager"

set your resolution there.

---

### Post by diablo75 on 2010-05-16
It turns out I didn't have to use the manual drivers.  After applying the latest updates (which included a kernel update) using Jockey actually successfully installed and setup the drivers.  Everything worked after a restart.

---

