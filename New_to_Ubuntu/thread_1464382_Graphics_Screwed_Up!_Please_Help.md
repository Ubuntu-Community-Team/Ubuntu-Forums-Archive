---
title: "Graphics Screwed Up! Please Help"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by Superlinkx on 2010-04-28
I was trying to optimize my graphics driver. (the ATI Radeon HD proprietary one) I got display errors. I tried putting my xorg.conf back to the way it was before, but that didn't help. I have tried reinstalling the driver, but it never seems to register that there is a graphics driver. While I have this issue, normally the GUI will never come up at all, just a blank screen. (normally purple, sometimes black) I need an easy way to put all the graphics back to original settings (the same when I first installed). Until then, I cannot update packages, install the drivers, or get any other packages. I have a ATI Radeon HD 4650 and am currently running 10.04 LTS RC 64-bit.

---

### Post by leonhook on 2010-04-28
have you tried this?
sudo dpkg-reconfigure xserver-xorg

---

### Post by Superlinkx on 2010-04-28
Yeah, that was the last thing I tried. I might try it again tomorrow. I think the problem lies with multiple system issues related to the improperly set graphics.

---

### Post by Grenage on 2010-04-28
You should be able to just remove xorg.conf, have you tried that?

---

### Post by Superlinkx on 2010-04-28
No, but I remember one time it didn't even show up when I went to edit it. Just some bad backups.

---

### Post by Grenage on 2010-04-28
I only mention it, because xorg.conf isn't usually required at all; one of the few (graphical) reasons for having one is when you're having EDID issues.

---

### Post by alphacrucis2 on 2010-04-28
Try 

```
sudo aticonfig --initial -f
```

---

### Post by Superlinkx on 2010-04-28
Ok, I tried those things. When I rebooted into normal mode, an error came up saying that it was started in low graphics mode. It can't find a driver and a couple other things. I tried continuing in low graphics mode, and now I am at my desktop. Unfortunately, I still cannot get my driver or any other apt-get commands.

---

### Post by Superlinkx on 2010-04-28
Ok, I got a little closer. Seems there is a broken package, fglrx-amdccle. I tried force removing it, but it always manages to pop back up after restarting. Also, whenever I restart, it still gives me the same graphics errors. It includes a reference to not being able to find fglrx. So somewhere, fglrx is still being referenced. Anyone know how to completely eradicate it?

---

### Post by Superlinkx on 2010-04-28
Ok, so I made some progress. I no longer get the error. I still cannot get completely rid of the ati driver. I found the uninstall script, but it seems it doesn't know what to do. I can't figure out how to force uninstall. I still have the CCC, so I know its still got its fingers in my system. I still cannot install it through hardware drivers, and currently cannot seem to get any other drivers loaded.

EDIT: I got it to force uninstall finally. That got rid of all the remaining ati crap. Hopefully when I reboot all will be well again. I'll post the results.

EDIT2: Everything is good now. I was able to reinstall the ATI driver through Hardware Drivers after the restart. I restarted again, and everything seems to be ok. Thanks for all your help. I was able to use pieces from all the responses to completely clean my system.

---

