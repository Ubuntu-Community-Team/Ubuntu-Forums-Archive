---
title: "[SOLVED] Dual Display Resolutions with Nvidia 7300"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by davester65 on 2008-12-27
Hey Guys, complete newb to ubuntu and linux, and the learning curve is huge but fun, i am running a dual monitor set up on 8.10 64 bit with an nvidia geforce 7300, i managed to figure out the dual display thing and got it working ok but my second screen doesn't give me the option of 1280x1024 (my native screen res) it defaults to 1024x768, yet it does give me 1280x1024 on my main monitor. Anyone know a fix for this? PS GUI fix preferred, am not confident with terminals yet!! Thanks

---

### Post by jimmy the saint on 2008-12-27
It is possible.  You can either run seperate x-servers, which means that you cannot drag windows from display to display, and it causes issues with firefox and a few other programms (you cannot have two instances running simultainously without a fairly complex workaround).
Another If you use the nvida-settings app, you can set different display sizes when you use twinview mode (nvidias version of xinerama) but there are significant issues with that as well.  Nautilus (which manages the desktop and all of its icons) is not aware of the mismatched monitors.  Essentially one big monitor is created, and so there is dead space around the smaller monitor.  Nautilus will still put icons there, so you can lose them.  It is a real pain.  

Here is the bug: [http://bugzilla.gnome.org/show_bug.cgi?id=60280](http://bugzilla.gnome.org/show_bug.cgi?id=60280)

I spent a year or so trying different configurations trying to get each one to work.  Eventually I discovered that Xfce does a much better job with mismatched monitors.  It recognizes the different resolutions and does not put icons where they shouldn't be.  You get xfce by using Xubuntu instead of Ubuntu.

Ultimately, my issues with dual monitors weren't resolved until I bought anther monitor so that I had two monitors with identical resolutions.  I got mine for 40 bucks on craigslist.  Gnome is pretty weak on dual monitors.  Hopefully this gets fixed soon.  As soon as bugzilla works (it is going SLOWWWWW) I will edit this post with the bug report, which is quite informative.

---

### Post by davester65 on 2008-12-27
Thanks for the info Jim, my monitors are identical and would like them both on 1280x1024 & i like the ability to drag from one screen to another.....oh well patience is a virtue they say:P, as a temp fix i set both monitors to 1152x864, i'll keep watching the forums. Thanks.

---

### Post by davester65 on 2008-12-28
Now solved this prob by searching around the forums and learning how to manually edit the xorg,conf file and resetting the second screen resolution.

The beauty of not knowing anything means i don't fear anything!

---

