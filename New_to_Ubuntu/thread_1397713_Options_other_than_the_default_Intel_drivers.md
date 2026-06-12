---
title: "Options other than the default Intel drivers?"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by Dreakon on 2010-02-03
Alright, my laptop with Ubuntu 9.10 runs pretty sluggishly.  My RAM isn't being used, my CPU isn't being used, there aren't even any programs running really.  So I'm thinking my integrated Intel graphics solution isn't working correctly with Ubuntu.  Specifically, it's a Intel GMA X4500HD Mobile (since it's a laptop).

Some people tell me "if the default drivers don't work, you're out of luck"... others tell me they're wrong and there are other options that could work better.  I've tried looking around for newer official Linux Intel GMA drivers, but never came up with any that were compatible/installable on Ubuntu.

Can anyone perhaps clarify a little more?  Is there anything I can try and/or any ideas that might get the system running a little smoother?

Thanks :)

---

### Post by ubunterooster on 2010-02-03
> **Dreakon said:**
> 

Can anyone perhaps clarify a little more?  Is there anything I can try and/or any ideas that might get the system running a little smoother?

Thanks :)

Generally you can't get alternative drivers.
Turn off all unneeded effects.
Hardware that sucks will always suck.

---

### Post by Dreakon on 2010-02-03
> **ubunterooster said:**
> Hardware that sucks will always suck.
Not in Windows apparently... :rolleyes:

I don't see how an Intel GMA 4500HD is capable of running that hog of an operating system known as Windows Vista, but apparently is too "sucky" (as you would so elegantly put it) to handle the absolute beast known as Ubuntu.

Thank you for putting me in my place.

---

### Post by falconindy on 2010-02-03
Generally people should avoid commenting on subjects they're not familiar with. While you can't get alternative drivers, you can enable KMS which may make your life easier.

This [wiki page](https://wiki.ubuntu.com/X/KernelModeSetting) should get you started.

Intel drivers are in the process of a huge makeover. While kernel 2.6.32 has been somewhat hellish on a few of the chipsets, 2.6.33 and the upcoming libdrm-intel and xf86-intel video drivers are looking quite promising for 2.6.33. Hopefully Ubuntu devs will be able to backport the 2.6.33 changes to Lucid.

---

### Post by Dreakon on 2010-02-04
I apologize for my previous post, I think it was unnecessarily hostile.

> **falconindy said:**
> While you can't get alternative drivers, you can enable KMS which may make your life easier.

This [wiki page](https://wiki.ubuntu.com/X/KernelModeSetting) should get you started.

Intel drivers are in the process of a huge makeover. While kernel 2.6.32 has been somewhat hellish on a few of the chipsets, 2.6.33 and the upcoming libdrm-intel and xf86-intel video drivers are looking quite promising for 2.6.33. Hopefully Ubuntu devs will be able to backport the 2.6.33 changes to Lucid.
Without going into too much detail, do you think by enabling KMS or updating the kernel or whatever the plan is here, I'll see immediate improvement to my desktop performance?  Or should I just bide my time and wait for Lucid?

I'm glad to hear that the Intel drivers are getting a huge makeover though!

---

### Post by 3rdalbum on 2010-02-04
The default Intel drivers are *the* Intel drivers - developed mainly by Intel.

Generally slow graphics don't cause application slowdown. Apart from CPU and memory use, there's another thing that can cause slowness, and that's I/O use. The 'iotop' program from the repositories can tell you if any particular program is using a lot of your system's IO capacity. The System Monitor applet in Gnome can also tell you if there's a lot of IO happening.

---

### Post by Dreakon on 2010-02-04
> **3rdalbum said:**
> The default Intel drivers are *the* Intel drivers - developed mainly by Intel.

Generally slow graphics don't cause application slowdown. Apart from CPU and memory use, there's another thing that can cause slowness, and that's I/O use. The 'iotop' program from the repositories can tell you if any particular program is using a lot of your system's IO capacity. The System Monitor applet in Gnome can also tell you if there's a lot of IO happening.
I don't really think that's the problem because this is an issue from the second I do a clean installation of Ubuntu... unless one of the default loaded programs is the problem... is which case wouldn't this be more of a widespread issue?

Besides, from this thread:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
(which no one has responded to me in :( )

and what has been said in this thread, I have to think the graphics can cause slowdown and that there are things I can do to improve performance... I just don't entirely understand how to do it and how it'll effect 9.10 (as the guide was written for 9.04).

---

### Post by falconindy on 2010-02-04
> **Dreakon said:**
> Without going into too much detail, do you think by enabling KMS or updating the kernel or whatever the plan is here, I'll see immediate improvement to my desktop performance?  Or should I just bide my time and wait for Lucid?
KMS allows the kernel to control the video driver, rather than letting a userspace program do it. It may not result in a **huge** magical performance gain, but it should be worth something. Bare minimum it allows you a native resolution framebuffer on boot and in a TTY, and reduces flickering when switching between TTYs. KMS is the "way ahead", and is enabled by default in 2.6.32 kernels and beyond.

> **Dreakon said:**
> I'm glad to hear that the Intel drivers are getting a huge makeover though!
Me too. My laptop (running Arch) is still currently running 2.6.31 because it refuses to play nicely with some of the changes in 2.6.32. I'd love to try out the 2.6.33 RCs on it, but I'm not enthused given how long it takes to compile a kernel on it (3-4 hours, versus 10 minutes on my c2d desktop). I've had to settle for reading lkml.org and RC changelogs.

---

