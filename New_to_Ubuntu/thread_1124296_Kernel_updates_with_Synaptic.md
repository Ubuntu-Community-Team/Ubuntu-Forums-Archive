---
title: "Kernel updates with Synaptic?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by landersohn on 2009-04-13
My question is whether the kernel version of Hardy 8.04 is ever updated via Synaptic or whether I need to manually download and install a newer kernel. I am running 1.6.24-23-generic and would like to upgrade to 1.2.25.

Thanks for your help

---

### Post by Dileeshvar on 2009-04-13
Generally if you are connected to Internet and as soon as you
log in there will be update manager showing you there are many updates
in that you could even find the kernel new version also !!

so this solves the problem I guess. 

:guitar:

---

### Post by drs305 on 2009-04-13
I checked the repositories and in my synaptic the -24 version is available, but only if the hardy-proposed repository is enabled (Settings, Repositories, Updates). Otherwise it is -23 on my machine (64-bit). I did not find -25 listed in either proposed or hardy-backports from the main server.

*Added for clarity: This post is for maintaining hardy but upgrading to a slightly newer kernel within hardy*.

---

### Post by snowpine on 2009-04-13
> **landersohn said:**
> My question is whether the kernel version of Hardy 8.04 is ever updated via Synaptic or whether I need to manually download and install a newer kernel. I am running 1.6.24-23-generic and would like to upgrade to 1.2.25.

Thanks for your help

Generally speaking, in the Ubuntu world, we get a new kernel by upgrading to a new release (like 8.10 II or 9.04 JJ). Ubuntu is "stable" once it is released, meaning you will never see a major kernel or package upgrade in Synaptics or update manager.

Let's talk about why you want to stick with 8.04 HH but install a newer kernel? Sometimes depending on the goal, there is an easier solution...

---

### Post by Kevbert on 2009-04-13
In Synaptic, go to Settings-Repositories and then click on the Updates Tab. Under Release Upgrade you should have 'Long Term Support releases only' selected. If you want to update to a newer Short Term Release (i.e. 6 month release such as 8.10) select 'Normal Releases' in the pull-down box. Now click on reload and you should have loads of updates including newer kernels. Otherwise you need to wait for 9.10.

---

### Post by landersohn on 2009-04-13
Thanks all for your help. 

snowpine, the problem I am trying to solve is a wireless problem with the iwl3945 module. My Dell refuses to work with some wireless networks and it looks as if the problem is in this module. Unfortunately it has been merged with the kernel in kernel version 24 and module code version 1.2.0. If I need a newer code for the module (which should fix my problem) I think I'll need a newer kernel. The 2.6.25 kernel has a newer iwl3945 module which should fix my problem

Upgrading to Intrepid overall is an option, however, I see a lot of posts of things not working and my overall impression is that Hardy is more reliable. Can you comment?

---

### Post by iris-n on 2009-04-13
It's hard to say that one version is more reliable than another. Too subjective.

Personally, I've had problems only with the Network fscking Manager. So I ditched it in favour of Wicd, and became a happy Intrepid user.

For home users, I don't think there is a benefit in staying with the LTS releases. You probably haven't bought support, and the upgraded software of the newer versions is more than worth the hurdles you may experience.

---

### Post by Jakey_TheSnake on 2009-04-13
Can you not manually download a newer iwl3945 module, then do the usual configure/make/make install and then modprobe?

---

### Post by snowpine on 2009-04-13
> **landersohn said:**
> snowpine, the problem I am trying to solve is a wireless problem with the iwl3945 module. My Dell refuses to work with some wireless networks and it looks as if the problem is in this module. Unfortunately it has been merged with the kernel in kernel version 24 and module code version 1.2.0. If I need a newer code for the module (which should fix my problem) I think I'll need a newer kernel. The 2.6.25 kernel has a newer iwl3945 module which should fix my problem

Upgrading to Intrepid overall is an option, however, I see a lot of posts of things not working and my overall impression is that Hardy is more reliable. Can you comment?

I really hate troubleshooting wireless issues; a lot of my own posts here on the forums are about wireless problems!

There is always more than one solution to a Linux problem. Upgrading the kernel is a definite possibility. Every Ubuntu kernel is available here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

However, I also see some extensive discussion about the iwl3945 module in Hardy: [http://ubuntuforums.org/showthread.php?t=765647](http://ubuntuforums.org/showthread.php?t=765647)

There are several possible solutions discussed in that thread, each with their pros and cons.

As to using Hardy vs. a more recent release, it is really a personal decision. I am a big proponent of "if it ain't broke, don't fix it," however, in your case, it *is* broke, so ask yourself whether the hassle of fixing the wireless problem is greater or less than the hassle of upgrading to Intrepid. :) I personally like to upgrade to the new version every 6 months; it is fun for me and I have a high tolerance for things screwing up.

---

### Post by landersohn on 2009-04-14
Thanks all,
lot's to try out which I will do over the next few days

---

### Post by BDNiner on 2009-04-14
You do have the option to compile the kernel yourself. It depends on how badly you want your wireless to work, and the effort you are willing to put in the achieve that goal. My solution was to go and buy a usb wireless adapter that does work. yes a cop-out but this was my stable computer! i have a testing one for all these other projects and stuff

---

### Post by Thelasko on 2009-04-14
> **snowpine said:**
> As to using Hardy vs. a more recent release, it is really a personal decision. I am a big proponent of "if it ain't broke, don't fix it," however, in your case, it *is* broke, so ask yourself whether the hassle of fixing the wireless problem is greater or less than the hassle of upgrading to Intrepid. :)
I agree with snowpine.  I stay with Hardy because everything works on my machine.

See if you can get your wireless working with the Intrepid/Jaunty live CD.  If you can get it working, I would say it's worth the upgrade.

---

### Post by rbaleksandar on 2009-04-21
Damn, I love you guys :D I posted yesterday about the same problem with Intel Wlan adapter. And a guy told me to update the kernel. Well, couldn't find the kernel in Synaptic.Now I can make an update, install a couple of packages he/she told me about and hope the problem will be solved. Thank you all! ;)

BDNiner, it's much better to try and fix the thing instead of going the "easy" way that might also bring more problems :)

---

