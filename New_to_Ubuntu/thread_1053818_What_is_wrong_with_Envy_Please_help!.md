---
title: "What is wrong with Envy? Please help!"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by birddog165 on 2009-01-29
I am trying to run
```
sudo envygt -t
```
to get the restricted drivers on my computer. I've got a GeForce 8600GT.

I get this:
```
+-------------------------------------------------+
 |                                                 |
 |             Welcome to EnvyNG                   |
 |    Developed by Alberto Milone (aka tseliot)    |
 |                                                 |
 +-------------------------------------------------+


 +-----------------------------------------------------------+
 |    EnvyNG Menu                                            |
 |                                                           |
 |    1 - Install the NVIDIA driver                          |
 |                                                           |
 |    2 - Uninstall the NVIDIA driver                        |
 |                                                           |
 |    3 - Install the ATI driver                             |
 |                                                           |
 |    4 - Uninstall the ATI driver                           |
 |                                                           |
 |    5 - Restart the Xserver                                |
 |                                                           |
 |    6 - Restart your computer                              |
 |                                                           |
 |    7 - Exit                                               |
 |                                                           |
 |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
 +-----------------------------------------------------------+
Please select one of the activities displayed above and press ENTER:

1
 +------------------------------------------------------------------------------+
 | Number | Candidate Version    | Installed Version | Compatible | Recommended |
 |------------------------------------------------------------------------------|
 | 0      | 177.82-0ubuntu0.1    | -                 | +          | -           |
 |------------------------------------------------------------------------------|
 | 1      | 173.14.12-1-0ubuntu4 | -                 | +          | +           |
 |------------------------------------------------------------------------------|
 | 2      | 96.43.09-0ubuntu1    | -                 | -          | -           |
 |------------------------------------------------------------------------------|
 | 3      | 71.86.04-0ubuntu10   | -                 | -          | -           |
 +------------------------------------------------------------------------------+
Please select the number corresponding to the desired driver and press ENTER 
(or type another number and press Enter to go back to the previous menu): 
1

Dowloading the packages...
Selecting previously deselected package nvidia-173-kernel-source.
(Reading database ... 192317 files and directories currently installed.)
Unpacking nvidia-173-kernel-source (from .../nvidia-173-kernel-source_173.14.12-1-0ubuntu4_i386.deb) ...
nvidia-173-kernel-source: Installing nvidia-173-kernel-source

nvidia-173-kernel-source: Preparing nvidia-173-kernel-source

nvidia-173-kernel-source: Unpacking nvidia-173-kernel-source

nvidia-173-kernel-source: Preparing to configure nvidia-173-kernel-source

Unpacking nvidia-glx-173 (from .../nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb) ...
nvidia-glx-173: Installing nvidia-glx-173

nvidia-glx-173: Preparing nvidia-glx-173

dpkg: error processing /var/cache/apt/archives/nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/xorg/modules/extensions/libglx.so', which is also in package xserver-xorg-core
Processing triggers for man-db ...
man-db: Running post-installation trigger man-db

Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb
Traceback (most recent call last):
  File "interface.py", line 432, in <module>
    a.mainMenu()
  File "interface.py", line 295, in mainMenu
    a.driverMenu('nvidia')
  File "interface.py", line 333, in driverMenu
    self.process(self.abstract.install, package)
  File "interface.py", line 391, in process
    myFunction(myArgs)
  File "/usr/lib/python2.5/site-packages/Envy/abstraction.py", line 155, in install
    self.pkg.install(packages, self.widget)
  File "/usr/lib/python2.5/site-packages/Envy/packagemanager.py", line 206, in install
    self.cacheUi.commit(UiFetchProgress(widget, self.isText), UiInstallProgress(widget, self.isText)) 
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 226, in commit
    res = self.installArchives(pm, installProgress)
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 201, in installArchives
    res = installProgress.run(pm)
  File "/usr/lib/python2.5/site-packages/apt/progress.py", line 216, in run
    res = pm.DoInstall(self.writefd)
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Traceback (most recent call last):
  File "interface.py", line 432, in <module>
    a.mainMenu()
  File "interface.py", line 295, in mainMenu
    a.driverMenu('nvidia')
  File "interface.py", line 333, in driverMenu
    self.process(self.abstract.install, package)
  File "interface.py", line 391, in process
    myFunction(myArgs)
  File "/usr/lib/python2.5/site-packages/Envy/abstraction.py", line 155, in install
    self.pkg.install(packages, self.widget)
  File "/usr/lib/python2.5/site-packages/Envy/packagemanager.py", line 206, in install
    self.cacheUi.commit(UiFetchProgress(widget, self.isText), UiInstallProgress(widget, self.isText)) 
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 230, in commit
    raise SystemError, "installArchives() failed"
SystemError: installArchives() failed

```

Please please please help me. I have no idea what is wrong?!?!?

---

### Post by sanderj on 2009-01-29
Why are you using Envy? For me, Ubuntu will take care of installing proprietary video drivers.

---

### Post by jerome1232 on 2009-01-29
You know I'm curious did you install envyng-core or envyng-gtk, I'm getting this sneaking suspicion that you need to install envyng-gtk. Everytime I've suggested installing envyng-core it broke, every time I said envyng-gtk it worked.

---

### Post by birddog165 on 2009-01-29
> **sanderj said:**
> Why are you using Envy? For me, Ubuntu will take care of installing proprietary video drivers.

You see, I tried that. I clicked on the 177 and then clicked ACTIVATE.
It says downloading and gets to ~60% and just stops. The window disappears and no drivers have been activated. :(

---

### Post by birddog165 on 2009-01-29
> **jerome1232 said:**
> You know I'm curious did you install envyng-core or envyng-gtk, I'm getting this sneaking suspicion that you need to install envyng-gtk. Everytime I've suggested installing envyng-core it broke, every time I said envyng-gtk it worked.

Yeah I have them both.
This is what's happening here.

I go and click install drivers. It installs them now [so thank you both] however, I restart and as the computer boots ubuntu [right after the Ubuntu progress bar screen] the graphics card physically resets 3 or 4 times. I know because I can hear the fan spin down. When it finally comes around, I get a pop up telling me that Ubuntu can't find my card and some stuff about uninformative stuff about Xserver. I get the option to start in "safe-mode" and so I'm like okay. Starting in this mode, the screen has shifted and inch down and right on my monitor. The space is filled with black and red static and the left side is part of the right side.
I uninstall the drivers, and I start Ubuntu normally and stuff works. Just as it would as a computer without the restricted drivers.

I have done this several times using either Envy or Ubuntu Restricted Drivers and I get the exact same thing. I have tried using every driver version too. Nothing.


The whole reason why I'm in this mess is because I wanted the 180 driver, rather than the 177. The 180 was only available via nVidia.com download. So I tried that and here we are :(

HELP!!

---

### Post by rustutzman on 2009-01-30
Just about the same thing happened to me but I never tried envy just the 180 driver. I ended up going into Synaptic and marking completely remove everything that had anything to do with nvidia. I rebooted and it took a couple of times but I was able to come up in a low graphics environment. From there I selected the 177 driver and was able to get that one going again.

There are a couple of threads on here concerning this issue. I sort of followed this one.
[http://ubuntuforums.org/showthread.php?t=1035873](http://ubuntuforums.org/showthread.php?t=1035873)
Read through the whole thread before you start and you should be able to get things working again.

Russ

---

### Post by birddog165 on 2009-01-30
> **rustutzman said:**
> 
Read through the whole thread before you start and you should be able to get things working again.

Thanks Russ. I'm gonna go to bed before I do this and work on it tomorrow morning. I'm really good with messing things up more than they should be right before I fall asleep, you I think I'm gonna call this a day and get it working tomorrow.

Thanks again, and I'll keep you posted with what happens.

---

### Post by Garyhans on 2009-01-30
I have NVidia 600 GT.. set up as Xserver on two monitors.... I did use Envy.. with hardy.. but this release I used.. the hardware.. 177.. with no probs..

---

### Post by birddog165 on 2009-01-30
Hmm, I'm considering a reinstall of ubuntu. Because this is just too much and nothing's working :(

---

### Post by birddog165 on 2009-02-04
So this is gonna probably upset who ever gets the same problem as me, but I really think that I brought this one myself by doing the manual install of the driver. I also have really wanted to use 64bit instead of the 32 that I'm on now. So I've got two things.

1) I'm gonna do a fresh install tomorrow. Kind of because I just don't want to bother trying to fix my mistakes, but also because I just want to be using the 64 for varius reasons.

2) NEVER ever try to install something because you think that you're better than the suggested way. Just use what they give you, and then get a separate partition for the fun stuff.

---

