---
title: "screen resolution"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by reivan on 2008-12-08
hi,

ubuntu 8.10 system-preferences-screen resolution allows a max of 960x600(16:10). the fedora core 10 install would also only allow a low maximum res. initially, but i was able to yum install system-config-display
to get different resolutions. i'm guessing if that had to be installed separately the same is true for ubuntu.? i'm very new at this and am experimenting with everything.thanks.R

---

### Post by lovelyvik293 on 2008-12-08
Just check the system->preferences->screen resolution

---

### Post by anewguy on 2008-12-08
I would try sudo dpkg -reconfigure xserver-xorg first (I think that's the syntax) to see if you can resolution there.

Also, what video card do you have and do you have the driver installed for it?

Dave

---

### Post by Averix on 2008-12-08
I've seen larger resolutions.  I think it has something to do with what your monitor is returning to the OS.  When the autosensing stuff works right, it's great.  When it fails, it's a major pain.  

I'm having a horrible time getting the right resolution out of a DVI port on several monitors.  What used to be convoluted, but possible by editing the xorg.conf file, seems to be nearly impossible with the new way of autosensing settings.  Does anyone have any good suggestions for 8.10 to tweak monitor/output settings?  Most of the suggestions in the forums are all centered around xorg.conf which really doesn't seem to do much of anything now.

---

### Post by anewguy on 2008-12-08
Yes, it does have to do with what your monitor is returning, or more in particular not returning, to the OS.  If you can find the specs for your monitor (vert/horiz ranges, resolutions at what frequency) you can still put those in xorg.conf in the monitor section.  If you need help with that after finding your specs, post back.

dave ;)

---

### Post by mapes12 on 2008-12-09
In 8.10 the "Screen & Graphics" utility has been removed and manually editing xorg.conf can have little effect. To get the utility back you need to download the packages.

Go to the following 2 links. At the bottom of each page is a link to allow the package to be downloaded. Make sure that, for guidance-backends you select the correct architecture for your computer. For displayconfig-gtk there is only one possible download for all architectures.

[http://packages.ubuntu.com/hardy/guidance-backends](http://packages.ubuntu.com/hardy/guidance-backends)

[http://packages.ubuntu.com/hardy/admin/displayconfig-gtk](http://packages.ubuntu.com/hardy/admin/displayconfig-gtk)

Once downloaded, click on the guidance-backends first, and you should be presented with the option 'Open with GDebi' or something similar. This installs the package on your system. Do the same for displayconfig-gtk package.

Then open a terminal and type:

```
gksudo displayconfig-gtk
```

The GUI should open for you to edit your settings.

---

