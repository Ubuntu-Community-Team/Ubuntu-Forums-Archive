---
title: "gtk Record My Desktop's captured video looks glitchy"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by diablo75 on 2011-05-11
Every now and then I record screen cast videos about how to do different things in Ubuntu.  This is the first one I've made since I installed 11.04 and the video that's captured has a lot of glitches in it, like... Say I had Firefox open full screen, and minimize it.  The video would fail to update the portions of the screen where the firefox window previously was, so it looks like Firefox is still open except where other parts of the interface have changed, like the launcher bar and it's icon's titles that fly out, which eat into and "repaint" the areas of the video that weren't updated.

I have "Full shots every frame" enabled in Record My Desktop but it doesn't help at all.

My video card is an nVidia Geforce 9600 GSO with 768 MB RAM.  Not sure what else to tell you about it...

Any ideas about what I might try to get a cleaner capture?

---

### Post by khelben1979 on 2011-05-11
Maybe it's because Ubuntu 11.04 uses a different version of the Record My Desktop software? But I'm sceptic.. Have you tried to turn off the unity interface to see if it helps?

[RecordMyDesktop - sourceforge.net]("http://sourceforge.net/projects/recordmydesktop/files/gtk-recordMyDesktop/").

---

### Post by diablo75 on 2011-05-11
> **khelben1979 said:**
> Maybe it's because Ubuntu 11.04 uses a different version of the Record My Desktop software? But I'm sceptic.. Have you tried to turn off the unity interface to see if it helps?

[RecordMyDesktop - sourceforge.net]("http://sourceforge.net/projects/recordmydesktop/files/gtk-recordMyDesktop/").

Well I would rather not because the video I wanted to make was going to be about Unity itself.

And I checked via Synaptic to see what version of recordmydesktop and it's the latest (version 0.3.8.1+svn602-1ubuntu3).

This probably has more to do with my video card drivers, and I don't know which ones are in use right now.  When I check Additional Drivers, it says "Current Version (Recommended)" is enabled.

---

### Post by khelben1979 on 2011-05-11
> **diablo75 said:**
> This probably has more to do with my video card drivers, and I don't know which ones are in use right now.  When I check Additional Drivers, it says "Current Version (Recommended)" is enabled.

Are you using nVidia drivers?

---

### Post by mikewhatever on 2011-05-11
The recommended Nvidia driver for your cards should be nvidia-current (aka 270.41.06). I hope you don't have multiple drivers installed, because that will cause problems. To find out, run **dpkg -l | grep nvidia**.

---

### Post by diablo75 on 2011-05-11
> **mikewhatever said:**
> The recommended Nvidia driver for your cards should be nvidia-current (aka 270.41.06). I hope you don't have multiple drivers installed, because that will cause problems. To find out, run **dpkg -l | grep nvidia**.

Here's the output:

```
ii  nvidia-common                         0.2.30                                     Find obsolete NVIDIA drivers
ii  nvidia-current                        270.41.06-0ubuntu1                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                       270.29-0ubuntu1                            Tool of configuring the NVIDIA graphics driver

```

---

### Post by diablo75 on 2011-05-13
Bump.

And is there a way to keep Unnity on screen while disabling some kind of special effects?  In other words can I keep Unity while disabling 3D effects?  Doing this might help with my recordings.

---

### Post by diablo75 on 2011-05-13
Bump.

I've also attached a screenshot of a video I tried to make a few days ago to show this glitching in action.  See the way the screen fails to repaint the wallpaper after I've minimized Firefox?  Only the portions of the screen that saw more action (I suppose the term is "damage") were painted; the areas where a little title bar flew out from hovering over the icons on the launcher bar on the left.

---

