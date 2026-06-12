---
title: "Installing Nvidia driver causes lack of desktop"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by Jinren on 2011-04-24
Hi all. I'm very new to Ubuntu and don't really understand what I'm doing, so:

I have been attempting to install Xubuntu 11.04 (Xubuntu because I like the look, not for specific reasons like performance). Having read that the default Nouveau drivers don't support 3D, and noticed that my preferred screen resolutions don't appear in the settings manager thing, I thought I should try to install the NVidia proprietary driver. My graphics card is a Geforce Go 7600.

The first thing I tried was to simply install nvidia-current from the Additional Drivers program. On reboot, no graphical interface appeared, just a list of checks ending a couple of entries after the one indicating it was starting GNOME display manager. Ctrl+Alt+F1 gives me a text terminal and I can stop gdm from it (so apparently it was running even though nothing was displayed?).

I have tried various options of removing nvidia- packages and installing others with dpkg -i (only ones I thought to download in advance, as I have no idea how to connect to the internet from a terminal). Doing this mainly seemed to completely break the system's ability to even show me a terminal (some of this was trying to mess around from a LiveCD environment using chroot). Fixed that by reinstalling, and back to square zero. I presume there's more to activating a driver than simply installing the package, especially when a different one is already installed... whoops. I tried 173 as well with presumably (I couldn't tell the difference) identical results.

The latest thing I have tried is to follow the instructions here: [http://ubuntuforums.org/showthread.php?t=1597178](http://ubuntuforums.org/showthread.php?t=1597178)

Again, didn't seem to make any difference: the list of tests appears, stops a couple of entries after gdm's one, and then when I get bored of waiting I can open a terminal.

I have tried to search, but don't really know how to specify my problem any better than the above, as I have no idea what's wrong (as far as I can see the graphics card should be supported?). I presume that this is a graphics/drivers issue rather than anything to do with Natty as I had a very similar problem a couple of years ago when I tried to install 8.10 (at that time, I simply gave up and went back to Windows).

I'm also totally confused by the problem in general: what *are* drivers? How are they installed and how does this interact with the package management tools? How do you choose between them or change which one is active? What's an xorg.conf and why doesn't it exist until after the Nvidia installer has run once? I don't understand any of these things (I don't expect answers to those here, this is just for context), nor how to find out the answers, which is making it difficult to understand what's gone wrong.

Thank you for reading.

---

### Post by mynameisnotbob on 2011-04-24
The problem might be the fact that it is xubuntu.

---

### Post by Jinren on 2011-04-24
Really? I thought that there was supposed to be no difference in the inner workings of the operating system.

Anyway, after some more searching I discovered there are such things as logs, and this part of Xorg.0.log looked important:
```
[    33.125] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    33.125] (==) NVIDIA(0): RGB weight 888
[    33.125] (==) NVIDIA(0): Default visual is TrueColor
[    33.125] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    33.128] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
[    33.128] (EE) NVIDIA(0):     check your system's kernel log for additional error
[    33.128] (EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
[    33.128] (EE) NVIDIA(0):     README for additional information.
[    33.128] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[    33.128] (II) UnloadModule: "nvidia"
[    33.128] (II) Unloading nvidia
[    33.128] (II) UnloadModule: "wfb"
[    33.128] (II) Unloading wfb
[    33.128] (II) UnloadModule: "fb"
[    33.128] (II) Unloading fb
[    33.128] (EE) Screen(s) found, but none have a usable configuration.
[    33.128] 
Fatal server error:
[    33.128] no screens found
```
Despite what it says, Chapter 8 of the readme doesn't appear to have an entry for that specific error message. There also wasn't anything appearing to correspond to this in kern.log.

Changing the Driver field of Section "Device" in xorg.conf to "nv", as many similar pages recommended, didn't do anything. Changing it to "vesa" did - a graphical desktop appeared, but with a maximum resolution of 800x600 (...at least I don't necessarily have to boot back into Windows to search for new information).

With that done I tried the Additional Drivers tool again, to make sure I'd actually tried the 173 version. It didn't work, but did give a slightly different error in the log:
```
[   193.095] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   193.095] (==) NVIDIA(0): RGB weight 888
[   193.095] (==) NVIDIA(0): Default visual is TrueColor
[   193.095] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   193.095] (**) NVIDIA(0): Enabling RENDER acceleration
[   193.096] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[   193.096] (II) NVIDIA(0):     enabled.
[   193.099] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
[   193.099] (EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
[   193.099] (EE) NVIDIA(0):     additional information.
[   193.099] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[   193.099] (II) UnloadModule: "nvidia"
[   193.099] (II) Unloading nvidia
[   193.099] (II) UnloadModule: "wfb"
[   193.099] (II) Unloading wfb
[   193.099] (II) UnloadModule: "fb"
[   193.099] (II) Unloading fb
[   193.099] (EE) Screen(s) found, but none have a usable configuration.
[   193.099] 
Fatal server error:
[   193.099] no screens found
```

Searching against "none have a usable configuration", "no screens found", etc. etc. led to a lot of threads without obvious resolutions. Oh dear.

---

### Post by mynameisnotbob on 2011-04-24
The inner workings are the same, but not the Xfce graphics.

---

### Post by Jinren on 2011-04-24
Yay! Found it!

Someone had a similar problem here: [http://ubuntuforums.org/showthread.php?t=1009612](http://ubuntuforums.org/showthread.php?t=1009612)

Turns out I too have a TV tuner card thing in this computer, so that sounded like it could be it, and it was. Since I never use the device to the point where I had forgotten it existed, instead of the solution proposed in that thread, I simply disabled it altogether, by using rmmod on the offending module ( cx18 ) and then adding a file to /etc/modprobe.d with a blacklist command (are both of these actions necessary?). And everything works!

And in the process, I've learned to like the terminal (and a bit about how to use it). Win-win.

---

### Post by mynameisnotbob on 2011-04-25
Terminal&#347; the best.

---

