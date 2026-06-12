---
title: "Get xorg.conf from LiveCD"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by wolverenstein on 2011-01-14
Hi there. I hope someone knows how to solve my problem. It's pretty straightforward: I have a new monitor and I don't know how to edit X Server files to get the proper new settings.  I tried Kubuntu from a LiveCD and it configures everything ok, but I failed locating xorg.conf: it isn't in /etc/X11. My idea is to use that file to update mine.  Anybody knows where is it? I'm not an Ubuntu user, so running the usual 'debian-esque' utilities to reconfigure the X Server won't work in my case.  Well... thanks in advance. Greetings from Latin America.  PS: if someone wants to know, I'm running Arch (I know, it's pretty lame to try that distro without knowing things like this).

---

### Post by elgordodude on 2011-01-14
Have you installed the latest video drivers?

This how to might help

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by Synthetic Sam on 2011-01-14
> **wolverenstein said:**
> Hi there. I hope someone knows how to solve my problem. It's pretty straightforward: I have a new monitor and I don't know how to edit X Server files to get the proper new settings.  I tried Kubuntu from a LiveCD and it configures everything ok, but I failed locating xorg.conf: it isn't in /etc/X11. My idea is to use that file to update mine.  Anybody knows where is it? I'm not an Ubuntu user, so running the usual 'debian-esque' utilities to reconfigure the X Server won't work in my case.  Well... thanks in advance. Greetings from Latin America.  PS: if someone wants to know, I'm running Arch (I know, it's pretty lame to try that distro without knowing things like this).
The reason there's no xorg.conf for the live cd is probably that it's using a kernel-mode-setting driver.  What graphics card do you have?

May also be helpful if you paste your old xorg.conf inside code tags so we can see what's going on.

---

### Post by Rubi1200 on 2011-01-14
You can't locate the file because it does not exist.

You can create your own xorg.conf file but we need to know what graphics card you have.

---

### Post by wolverenstein on 2011-01-14
@elgordodude: Yep, all upgraded to the latest.
@Synthetic Sam: I have a nVidia GeForce 8400GS with proprietary drivers.
@Rubi1200: I wasn't aware of that...

Thanks for the answers. I was troubled about the "modeline" stuff (my old xorg.conf included those lines), but today I read that for new monitors those options are obsolete... so I deleted them. Also, I added my desire resolution in the screen section, and everything is working fine. But I can't set the optimum refresh rate...

At this point I don't know if it's ok to continue trying to solve the problem in this thread because it departs from the original question. So, let's go back to that: is it possible to generate a xorg.conf file from a (X)Ubuntu LiveCD?

Thanks!

PS: anyway, if someone wants to help, I'm using KDE. The fact is that, in "System Settings", it only offers 50 Hz in the refresh rate options. Strange because in xorg.conf I wrote 'VertRefresh 56.0 - 75.0'. The optimum is 60, as the manual and nvidia-settings says:

```
$ nvidia-settings -nt -q RefreshRate
59.95 Hz
```Changing VertRefresh to 60 makes no difference. KDE keeps offering 50... only.

One more thing: the "NVIDIA X Server Settings" says that I'm using the monitor at 60 Hz. Weird.

---

