---
title: "GRRR!  Buttons don't work"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by myolbug on 2010-01-08
I don't know WTF is going on, but after this latest kernel upgrade, flash is glitchy and buttons don't work.

For example, some videos I can't watch.  I click the play button and nothing happens.  Another thing, while watching a youtube video, I try and click HD or full screen and the buttons look like they are being pressed, but again, nothing happens.  This button thing is on other sites as well.

I feel like I am using Windows ME!  I am starting to double think this whole Ubuntu thing.  I have been having a lot of trouble with it.

I am current on all the updates and I have the latest version of flash.

---

### Post by argos3016 on 2010-01-08
Are you sure that is not the mouse?(seriously)

---

### Post by running_rabbit07 on 2010-01-08
Restart and use the previous kernel. It would also be helpful to know which Ubuntu you are using.

---

### Post by argos3016 on 2010-01-08
Any result (rebooting?)

---

### Post by myolbug on 2010-01-08
> **argos3016 said:**
> Are you sure that is not the mouse?(seriously)

I get what you're saying, but there is an indication of the button being pushed, ie, changes color, etc, but nothing happens.  It is mostly happening on Flash objects.  Such as Youtube and other flash objects.

---

### Post by argos3016 on 2010-01-08
No idea

---

### Post by myolbug on 2010-01-08
> **running_rabbit07 said:**
> Restart and use the previous kernel. It would also be helpful to know which Ubuntu you are using.

Sorry for the lack of info, I have ubuntu 9.10 64 bit with the latest kernel, whichever was just released. I rebooted it after installing the new kernel.

---

### Post by running_rabbit07 on 2010-01-08
> **myolbug said:**
> Sorry for the lack of info, I have ubuntu 9.10 64 bit with the latest kernel, whichever was just released. I rebooted it after installing the new kernel.

I would recommend just restarting and selecting the -16 kernel for a few days, then try again and run updates to see if it is fixed. If you haven't done so already, you should file a bug report so that the devs know about the problem. For the bug report you will need to include that the kernel is 2.6.31-17.

---

### Post by myolbug on 2010-01-10
> **running_rabbit07 said:**
> I would recommend just restarting and selecting the -16 kernel for a few days, then try again and run updates to see if it is fixed. If you haven't done so already, you should file a bug report so that the devs know about the problem. For the bug report you will need to include that the kernel is 2.6.31-17.

I have done this.  Almost all of the Flash glitches are gone.  I'll compile a bug report.

---

### Post by jmszr on 2010-01-10
myolbug,

The bug has already been reported: [https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all) . Some  workarounds are shown there.

Also, Ubuntu Geek has a post about it: [http://www.ubuntugeek.com/fix-for-flash-is-not-recognizing-mouse-clicks.html](http://www.ubuntugeek.com/fix-for-flash-is-not-recognizing-mouse-clicks.html)

---

### Post by 3rdalbum on 2010-01-10
If you click outside the Flash movie, the next time you click inside it your click will be recognised.

What browser are you using?

---

### Post by argos3016 on 2010-01-11
If you can change to kernel 14 , because 17 caused me a xorg crash (and internet and mouse doesn't work)

---

