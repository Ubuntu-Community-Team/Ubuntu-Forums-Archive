---
title: "ATI Radeon Driver Question (8.10)"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Syndacate on 2009-06-05
Hey,

I just installed 8.10 again (9.04 was giving me too many problems), but now I don't have my old nvidia geforce 7600GS anymore (the fan went on it and I haven't been able to find a new one), but rather an **ATI 9800SE**.  The system is fully updated and the restricted/proprietary drivers installed fine, but I have a 24" syncmaster monitor which has a default resolution of 1920x1200, the highest this will go is 1600x1200.

Anybody have any suggestions?

Thanks in advance.

- Greg

---

### Post by Mark Phelps on 2009-06-05
Try opening a terminal and typing "sudo displayconfig-gtk".  It should bring up a panel that will allow you to manually choose your desired resolution.

If that doesn't work, you can try using xrandr from a console to set your resolution, as follows:
1) Press Ctrl-Alt-F1 to kill X and start the console
2) Type "xrandr -s 1920x1200" 
3) Type "exit"
4) Press Ctrl-Alt-F7 to restart X.

---

### Post by Syndacate on 2009-06-05
> **Mark Phelps said:**
> Try opening a terminal and typing "sudo displayconfig-gtk".  It should bring up a panel that will allow you to manually choose your desired resolution.

If that doesn't work, you can try using xrandr from a console to set your resolution, as follows:
1) Press Ctrl-Alt-F1 to kill X and start the console
2) Type "xrandr -s 1920x1200" 
3) Type "exit"
4) Press Ctrl-Alt-F7 to restart X.

displayconfig-gtk can't be found, although when trying to install via aptitude it tells me it's referred to by another package, searching for the package via aptitude with a regex that should match it (**-gtk$**) doesn't show it.

As for the xrandr method, that didn't do anything, I got a message that said "Can't open display." - then my mouse took a **** and restarting the X server twice didn't fix it, I had to reboot, still 1600x1200.

Anybody else have some suggestions?  I'd greatly appreciate it.  I wouldn't even mind if it was this unclear and the right ratio, but circles look like ovals b/c it's so far out of whack...

I'm starting to think this is a limitation by ATI's proprietary drivers...

---

### Post by Syndacate on 2009-06-05
Update:
```
lsmod | grep radeon
```

Doesn't display any results.  I'm assuming the module isn't loading.

When I try to load it with:
```
modprobe radeon
```

I get the following error:
```
WARNING: Error inserting drm (/lib/modules/2.6.27-14-generic/kernel/drivers/gpu/drm/drm.ko): Cannot allocate memory
FATAL: Error inserting radeon (/lib/modules/2.6.27-14-generic/kernel/drivers/gpu/drm/radeon/radeon.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Anybody else have problems with the proprietary ATI drivers in 1.5.2 of the X server?

I'd like to go with a free alternative, but the OSS drivers I hear, for ATI cards have crappy support.

Right now, according to my xorg.conf file, I'm using fglrx, which is apparently the catalyst driver, though I thought they showed up as radeon?

I'd like to use the proprietary ones as they typically work better (and yes, I realize this is against the whole "linux way", but I like to get the best out of my cards, no flame plz).  

Jeez, this would all be solved once I find a cooler for my 7200GS.

---

### Post by porchrat on 2009-06-05
> **Syndacate said:**
> Update:
Right now, according to my xorg.conf file, I'm using fglrx, which is apparently the catalyst driver, though I thought they showed up as radeon?

I'd like to use the proprietary ones as they typically work better (and yes, I realize this is against the whole "linux way", but I like to get the best out of my cards, no flame plz).  

"fglrx" is the driver portion of the catalyst package that you download from ATI. In other words, the entire package is called Catalyst, the driver that comes with it is called fglrx and the GUI for changing settings is called the Catalyst Control Centre.

Also, who told you that using proprietary drivers is against the linux way?

Use whatever works, the standard Ubuntu ATI drivers are terrible, a lot of people use the proprietary ATI drivers.

What does the 'fglrxinfo' command output?

---

### Post by Syndacate on 2009-06-06
> **porchrat said:**
> "fglrx" is the driver portion of the catalyst package that you download from ATI. In other words, the entire package is called Catalyst, the driver that comes with it is called fglrx and the GUI for changing settings is called the Catalyst Control Centre.

Also, who told you that using proprietary drivers is against the linux way?

Use whatever works, the standard Ubuntu ATI drivers are terrible, a lot of people use the proprietary ATI drivers.

What does the 'fglrxinfo' command output?

Lots of people believe using proprietary drivers is against the Linux way.  Linux is meant to be in totality, 100% free, not in cost, but in software licensing.  I'm sure if torvalds was here he'd be shaking his head. :(

The code produced by the 'fglrxinfo' command:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 SE
OpenGL version string: 2.1.8087 Release

```

I'm thinking this is a driver issue, as I'm having the same issue with the same drivers in Fedora.

I'm going to have ordered another cooler for my Nvidia Monday, that'll most likely fix this problem, I'm not sure if there's anything else that can be done about it, as you can see by the above, it's installed correctly and the like.  Though if you have any other suggestions still feel free to suggest.

---

