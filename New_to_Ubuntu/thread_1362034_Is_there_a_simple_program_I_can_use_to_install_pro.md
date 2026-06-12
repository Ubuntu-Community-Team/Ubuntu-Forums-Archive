---
title: "Is there a simple program I can use to install programs?"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by simpleblue on 2009-12-22
I wanted to install some easy sound programs like:

XMMS
Amarok
BMP

But I run into having to type a massive amount of scripts. I know that the Ubuntu Software Centre is good for this, but mine still doesn't work:

[http://ubuntuforums.org/showthread.php?t=1361515](http://ubuntuforums.org/showthread.php?t=1361515)

I'm still working on that though...

If anyone has suggestions on where I can retrieve an installer programs like Ubuntu Software Centre or knows where I can easily download and install programs like the music ones above it would be greatly appreciated.

Thanks

---

### Post by audiomick on 2009-12-22
Have you tried the synaptic package manager? I think that is still there in a 9.10 fresh install. system> administration> synaptic package manager

I can find xmms and amarok, but not bmp

---

### Post by oldos2er on 2009-12-22
Synaptic Package Manager, or in a terminal run ```
sudo apt-get update && sudo apt-get install xmms amarok
```

---

### Post by t0p on 2009-12-22
Try **Synaptic Package Manager**.  You'll find it under **System > Administration > Synaptic Package Manager**.

When Synaptic opens, click on its search button.  Then type the name of an application into the box that appears.  Synaptic will search for that package, then you can click on it and select to install.  Do this for all the apps you want, then click on Apply.  The programs will install.

Alternatively, you can search for the type of app you want.  For instance, type "music player" into the search box, and it will pull up a list of apps.  You can look through the list, click on the ones you want and select Install, then cleck on Apply.

---

