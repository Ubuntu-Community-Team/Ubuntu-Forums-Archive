---
title: "deleted gnome media"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by mustard greens on 2009-11-12
Ive accidentally removed gnome media through synaptic and now it will not let me reinstall it saying some dependencies are not available.  any suggestions?

---

### Post by philinux on 2009-11-12
> **mustard greens said:**
> Ive accidentally removed gnome media through synaptic and now it will not let me reinstall it saying some dependencies are not available.  any suggestions?

You'll have to post back with the full errors.

---

### Post by mustard greens on 2009-11-12
not sure what you mean.  there were no error messages involved.  the package which I deleted is no longer available in synaptic, and I am unsure of the original message, but it was something like "certain dependencies unavailable as they were part of the installation"

---

### Post by mustard greens on 2009-11-12
I am downloading the live CD in hopes that the package is on there.

---

### Post by philinux on 2009-11-12
> **mustard greens said:**
> I am downloading the live CD in hopes that the package is on there.

Right ok. Here's what to do. Forget the live cd although its handy if you haven't got one. The app is in synaptic.

Open a terminal. Applications>accessories>terminal.

Copy and paste from below.

```
sudo apt-get install gnome-media
```

Post back what it spits out.

---

### Post by mustard greens on 2009-11-12
ok so below is the print out from terminal which pretty obviously says that the package I deleted is both obsolete and unavailable which is all well and good as I do have the recommended replacment, but...

the issue I was having was that I accidentally deleted the volume control applet from my top panel, and it was not available to replace it through the panel applet preferences.  so I had uninstalled the gnome media package in an attempt to reinstall and therefore retrieve my volume controller.  I was able to place an applet titled volume control from system/preferences/volume control, but it doesnt provide the convenient slider of the original applet.  any help in this direction would be much appreciated.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-media is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgnome-media0 gnome-media-common
E: Package gnome-media has no installation candidate

---

### Post by NightwishFan on 2009-11-12
try:

```
sudo apt-get update && sudo apt-get install gnome-media
```

Edit: On the volume applet, I believe you have to start it manually. I am not sure how, I will get back to you.

---

### Post by mustard greens on 2009-11-12
an interesting development is that since I deleted the supposedly unnecessary package the volume control which I was able to place in the panel is no longer working and tells me 

failed to execute child process "gnome-volume-control" (No such file or directory)

what have I done? #-o

---

### Post by NightwishFan on 2009-11-12
[http://packages.ubuntu.com/karmic/gnome-media](http://packages.ubuntu.com/karmic/gnome-media)

It looks like it is still there. Perhaps you should select a different server under software sources. You can choose to automatically find the fastest one.

---

### Post by philinux on 2009-11-12
> **mustard greens said:**
> ok so below is the print out from terminal which pretty obviously says that the package I deleted is both obsolete and unavailable which is all well and good as I do have the recommended replacment, but...

the issue I was having was that I accidentally deleted the volume control applet from my top panel, and it was not available to replace it through the panel applet preferences.  so I had uninstalled the gnome media package in an attempt to reinstall and therefore retrieve my volume controller.  I was able to place an applet titled volume control from system/preferences/volume control, but it doesnt provide the convenient slider of the original applet.  any help in this direction would be much appreciated.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-media is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgnome-media0 gnome-media-common
E: Package gnome-media has no installation candidate

Post back your sources list.

```
cat /etc/apt/sources.list
```

---

### Post by mustard greens on 2009-11-12
ok, so I did switch mirrors.  apparently my local mirror was having issues and was stalling out.  ran the update and was able to reinstall gnome media.  volume control is back up and running, but still cant find how to bring back original applet.  thank you for all of the help so far.  does anyone know where to find the original volume applet?  the one with just a slider for master volume.

---

### Post by mustard greens on 2009-11-12
@ philinux

I think the source issue has been overcome, but here is the print out of sources.

deb [http://ubuntu.wallawalla.edu/ubuntu/](http://ubuntu.wallawalla.edu/ubuntu/) karmic main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security universe main multiverse restricted
deb [http://ubuntu.wallawalla.edu/ubuntu/](http://ubuntu.wallawalla.edu/ubuntu/) karmic-updates universe main multiverse restricted
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

I had been using the U of O mirror but they seem to be having difficulty.

---

### Post by mustard greens on 2009-11-12
Im going to mark this thread solved and open a new thread regarding the volume applet.  thanks to all for their support.

---

