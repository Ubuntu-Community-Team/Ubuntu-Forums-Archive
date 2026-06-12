---
title: "Low graphics mode, i915.modeset and graphics drivers."
date: 2010-09-09
forum: New to Ubuntu
---

### Post by nexus0123 on 2010-09-09
Hi everyone...

I'm using 10.04 on a very old laptop with the Intel 82852/82855 chipset, and have had a lot of problems with it. However, I've been using workarounds which seem to fix problems here and there. I just had a few questions regarding these workarounds, for learning purposes:

_Question 1._ **What is i915.modeset=1 in Grub?**
I always got a blank screen when starting up Ubuntu (non Low graphics mode). Then I found a fix on the net that told me to add that line to the /etc/default/grub file and everything loaded fine. I know it has something to do with the i915 graphics drivers, but not so clear.

_Question 2._ **What's the difference between low graphics mode and regular mode?**
For some time, whenever I played an MP3 in Totem, it would crash (blank screen, something to do with X server). Then, when I started up in low graphics mode, the MP3 was able to play! So I want to know exactly what settings are different / disabled in low graphics mode which allows me to play the MP3s. Is there a command I can run in terminal which lists all the settings, like "lspci -v"?

_Question 3._ **How do I change the graphics drivers / settings I am using?** (in the command line, without installing some GUI)
According to "lspci -v", the "Kernel Module" I'm using for the graphics controller is i915. Is there any way to change this to another version since I really should be using i828 or something like that. Just wanted to test out other drivers / settings and see if they're better.

That's all for now. Thanks in advance!

---

### Post by oldfred on 2010-09-09
I do not have an answer but possibly some places to look.

You say old computer, how much memory and is the memory shared with the video controller. Perhaps when in best video you are using more memory and then do not have enough for totem? How much swap but then system will get very slow.

What does top in terminal show? is memory fully used? What applications  are running and how much memory.

There are not video driver for every version, just major families of video cards.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0

---

### Post by nexus0123 on 2010-09-09
I have 2gb of memory (shared between graphics and RAM), so I don't think that's an issue. System Monitor tells me only about 10% is in use. Starting Totem barely moves it (15mb only). And the MP3 I'm playing is only about 7mb, so definitely not hitting any limit.  I don't think there's any way for me to monitor memory usage, given that the moment I open the file, it crashes.

---

