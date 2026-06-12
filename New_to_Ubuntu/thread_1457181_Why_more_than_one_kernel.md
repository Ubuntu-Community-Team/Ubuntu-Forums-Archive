---
title: "Why more than one kernel"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by Alexx86 on 2010-04-18
Hey,
I still don't really understand why I would install a second kernel for the same GNU system.
When exactly would you need one system but two options in your bootloader? If I would see an example, I might finally understand :)
Also, links to further reading material are very appreciated.
Thanks,
 Alex

---

### Post by cascade9 on 2010-04-18
As soon as you get a new kernel you have 2 kernels (minimum). So unless you never update thje kernel, you will have two at some point. 

Its handy in case you ever have trouble with a kernel- you can then just change from kernel x.x.yy to kernel x.x.xx and the problem is gone. I've done this in the past when I have had issues with a newer linux kernel and nvidia-kernel.

---

### Post by coffeecat on 2010-04-18
An updated kernel is included in a system update from time to time - usually a bugfix or security patch. The installer retains the older kernel in case you have problems with your hardware and the newer kernel, so that you can boot into the previous version.

After a time you will collect quite a number of kernels. If you uninstall the older ones using Synaptic, the grub menu entries will be automatically removed, but it is advisable to retain the last working kernel - just in case.

---

### Post by howefield on 2010-04-18
It isn't compulsory to install extra kernels. :)

Sometimes the kernel is updated and added to the repository, in which case you will get it through the regular updates leading to a build up of kernels on your system, nothing to worry about unless something doesn't work, in which case you can boot with the last known working kernel.

One example of installing extra kernels might be to take advantage of more RAM than the regular 32 bit can, so you might install the server kernel, which is PAE enabled.

There are probably better examples than that, but you get the idea.

---

### Post by mcduck on 2010-04-18
In case the new kernel that comes as an update doesn't, for some reason or other, work correctly on your computer you'll be able to boot to the old kernel instead and still ave a working system.

You can just uninstall the old kernel after you have confirmed that the new one is working correctly.

---

### Post by Alexx86 on 2010-04-18
So if I wanted to compile my own kernel, I can't break anything because the current, old one still remains in /boot/. Nice.
I'm having problems fixing my WLAN on a Backtrack Linux (built from Ubuntu), and found this:
[http://comments.gmane.org/gmane.linux.drivers.bcm54xx.devel/10557](http://comments.gmane.org/gmane.linux.drivers.bcm54xx.devel/10557)
Now I'm trying to build a second kernel to see if that lib80211 (whatever it is) is included.

---

### Post by Dude-PWB- on 2010-04-18
Everyone has a different computer system so while a new kernel might be good for most users, it certainly has the possibility of not working for some systems, it's just the nature of non proprietary systems.

At least if you have an issue with a new kernel, you can always revert back to what worked earlier in order to find a solution, or report the problem.

---

### Post by coffeecat on 2010-04-18
> **Alexx86 said:**
> So if I wanted to compile my own kernel, I can't  break anything because the current, old one still remains in /boot/.  Nice.

That's the beauty of Linux. :)

When I was running Gentoo, I compiled and amassed up to a couple of  dozen kernels trying to get iptables working. Before I deleted the  faulty ones, that is. I was glad I hadn't follow the Gentoo handbook's  advice of having a separate /boot partition of only 32MB. :rolleyes:

Don't forget that the "extra" kernels will also have files in  /lib/modules and /usr/src.

---

### Post by huygens on 2010-04-18
You can specialise your kernels. For instance, you are a musician and you definitively need a low latency kernel so you do not have clinks and clinches while hearing a record.
However, a low latency kernel might not be that confortable for day-to-day internet use.

A solution is you have 2 kernels installed, one low latency and one for general purpose. When you go to the studio with your laptop, you select the low latency kernel. However, you have the generic one as default, so when you go home and just want to see how your friends/family is doing you just boot the machine.

---

### Post by Alexx86 on 2010-04-18
> **huygens said:**
> You can specialise your kernels. For instance, you are a musician and you definitively need a low latency kernel so you do not have clinks and clinches while hearing a record.
However, a low latency kernel might not be that confortable for day-to-day internet use.

A solution is you have 2 kernels installed, one low latency and one for general purpose. When you go to the studio with your laptop, you select the low latency kernel. However, you have the generic one as default, so when you go home and just want to see how your friends/family is doing you just boot the machine.

Awesome, thanks.
Does anyone know of a "definite" guide on compiling a special kernel? I've done it before, but that was years ago. Now I don't even know what:
> 
I rebuilt my kernel (using -rc2 sources), and while configuring, I
noticed that LIB80211 wasn't being built.  I enabled it

means.
I need to download the sources (how?), and then 'make menuconfig' or something... it really has been a long time :)

---

