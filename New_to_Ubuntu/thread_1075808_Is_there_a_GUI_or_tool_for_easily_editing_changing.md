---
title: "Is there a GUI or tool for easily editing changing display?"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by wiseheart on 2009-02-20
Hi, I'd like to set up Ubuntu to have similar display capability to when I am booted in Windows. In Windows, I can easily select the display resolution and can select sizes up to 1600x1200 without problem by right clicking on the screen and selecting properties. I can also plug in a second monitor and bring it up using the same process. 

I cannot find anything that says how to do this in Ubuntu without editing the x conf file. This also seems to involve guessing what resolutions my display will handle? 

Are there any tools that would make this an easier process? I am afraid that I will mess something up and get left with no display at all. 

As far as specifics for my computer, this is an IBM T41 Thinkpad, with the following graphics card:
description: VGA compatible controller
product: Radeon Mobility M7 LW [Radeon Mobility 7500]

and here is fglrxinfo:
d@d-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2

In this current setup I am limited to 1280x720 and I am unable to dual-monitor, the second monitor will just display what is on the laptop screen. 

Thanks for any help :)

---

### Post by spiderbatdad on 2009-02-20
System>>Preferences>>Screen Resolution. The program DisplayConfigGtk in synaptic might help you.
I'm afraid for dual monitors you are going to have to edit xorg. So, you make a copy called xorg.backup and it is there for you. You boot into recovery if necessary and move the backup to the original if your system become unbootable. Make sure you understand terminal commands for moving and copying files...ie, if you were in recovery, you would be root, so sudo would not be needed:```
# cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
# mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf 
```There are some guides for this...see what I can find. IDK if there are any solutions that dont require nvidia graphics card.
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)
[https://wiki.ubuntu.com/DisplayConfigGTK](https://wiki.ubuntu.com/DisplayConfigGTK)

---

### Post by spiderbatdad on 2009-02-20
edited previous post

---

### Post by wiseheart on 2009-02-20
> **spiderbatdad said:**
> System>>Preferences>>Screen Resolution. The program DisplayConfigGtk in synaptic might help you.
I'm afraid for dual monitors you are going to have to edit xorg. So, you make a copy called xorg.backup and it is there for you. You boot into recovery if necessary and move the backup to the original if your system become unbootable. Make sure you understand terminal commands for moving and copying files...ie, if you were in recovery, you would be root, so sudo would not be needed:```
# cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
# mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf 
```There are some guides for this...see what I can find. IDK if there are any solutions that dont require nvidia graphics card.
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)
[https://wiki.ubuntu.com/DisplayConfigGTK](https://wiki.ubuntu.com/DisplayConfigGTK)

Thanks, I tried Screen Resolution before and it does not help as it only gives me two options, 1040x768 and 800x600. Ill try getting the displayconfigGtk. 

I'd really like to try to find a solution that cannot make my system unbootable (or at least as a minuscully low chance of doing so).

---

### Post by spiderbatdad on 2009-02-20
Not sure the previous post was clear, as I showed cp command in recovery mode with mv command. The point is this...before you touch your xorg.conf file, make a backup copy of the original. If you end up with a problem just replace the current copy with the backup, using the mv command.

---

### Post by SunnyRabbiera on 2009-02-20
If you are using ibex then displa config is gone... for very stupid reasons if you ask me, and there seems to be no replacement in site for jaunty.

---

### Post by wiseheart on 2009-02-20
Thanks again for the displayconfig-gtk (note that it has a dash in it, couldn't apt-get it without the dash) 

It is what I was looking for. However, my IBM T41's model, 2373, is not listed as an option. I wonder if this means I need to find a driver for it or if I can use a similar model's driver. 

I tried testing it after setting it to a higher resolution using the selection for a similar model, and I got a screen with lines going diagonal across, with an x shaped cursor, and the dialog box asking if i wanted to keep those settings. I'm assuming that the display was wrong for that selection based on the background, unless it shows up like that for all test? 

Thanks for your time.

---

### Post by SunnyRabbiera on 2009-02-20
> **wiseheart said:**
> Thanks again for the displayconfig-gtk (note that it has a dash in it, couldn't apt-get it without the dash) 

It is what I was looking for. However, my IBM T41's model, 2373, is not listed as an option. I wonder if this means I need to find a driver for it or if I can use a similar model's driver. 

I tried testing it after setting it to a higher resolution using the selection for a similar model, and I got a screen with lines going diagonal across, with an x shaped cursor, and the dialog box asking if i wanted to keep those settings. I'm assuming that the display was wrong for that selection based on the background, unless it shows up like that for all test? 

Thanks for your time.

Me I ignore the default monitor detection, my monitor is detected as "plug and play" in most distros but I always change it to "generic" as it never works the way I want it to.
I suggest trying one of the generic monitor settings.

---

### Post by wiseheart on 2009-02-20
> **SunnyRabbiera said:**
> Me I ignore the default monitor detection, my monitor is detected as "plug and play" in most distros but I always change it to "generic" as it never works the way I want it to.
I suggest trying one of the generic monitor settings.

I tried this before, and what I get is a screen filled with cross-hatches and a dialog box asking if I would like to keep that setting. I'm assuming I should be seeing the normal desktop and not a bunch of cross hatches if things were working normally yes?

---

### Post by wiseheart on 2009-02-20
I tried looking at the guide for Xinerama at [http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624) and I looked at the xorg.conf file 

However, I am a bit worried on moving forward as in that guide, it actually shows the correct card for the device, however in my xorg.conf file I have the following as the Device: 

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

---

### Post by spiderbatdad on 2009-02-20
No guts no glory! The frist thing to do is BACKUP your original xorg! Understand how to recover by moving the back up to replace the edited one if need be. nuff said.

---

### Post by SunnyRabbiera on 2009-02-20
> **wiseheart said:**
> I tried this before, and what I get is a screen filled with cross-hatches and a dialog box asking if I would like to keep that setting. I'm assuming I should be seeing the normal desktop and not a bunch of cross hatches if things were working normally yes?

Yes, maybe you should play around none the less, but be careful.
It might be your card at issue too, but its hard to say.

---

### Post by wiseheart on 2009-02-20
> **SunnyRabbiera said:**
> Yes, maybe you should play around none the less, but be careful.
It might be your card at issue too, but its hard to say.

Well I edited xorg.conf based on instructions in another thread, and I got the right resolution for the external monitor, but it is just showing up as 1 screen, so my laptop lcd is a cutoff version of what is on the external monitor. 

I then tried displayconfig-gtk to set one as primary screen and one as secondary. This resulted in a black screen and fortunately a popup asking if I wanted to boot into low graphics mode, which was barely visibile in top left hand corner. I did this, and then went into terminal and copied over the xorg.conf backup. Now, I am back to the previous state. 

I'd like to stress that, this is not a problem with the video card, at least not in the sense of its capabilities. I can dual-screen in Windows with no problem and quite easily by just right-clicking on Desktop and clicking on a few boxes. It seems like this is either a driver issue, or that I need to try one of dual-monitor solutions listed in another one of the external links or that Ubuntu doesn't have support for this particular setup (Neither my IBM T41 model or my external lcd model are available in the displayconfig-gtk gui) 

Thanks for the help though.

---

