---
title: "Problems with 2-6-32-21-generic kernel?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by ben1986 on 2010-05-01
Hi everyone, is anyone having freezing problems running the new kernel for Lucid?  Luckily for me I used a 9.10 live cd to install, and upgrade from that so I'm using the 2-6-31-21 kernel right now with *almost* no problems.

When I moved from Intrepid to Jaunty I had the same issue with the fresh kernel, and so I installed a new one, which fixed the freezing but nobbled my graphics card.  Now I have compiz config settings manager making everything whiz and whir I am loathe to add a new kernel in case I lose everything again.

Has anyone else had problems? I'm considering just removing the new kernel, but if I do that will update manager badger me to upgrade all the time?  Will it cause trouble later?

---

### Post by dracayr on 2010-05-01
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492)

aparrently there are stability issues on some chipsets, although I haven't experienced anything of that, even though I have a 855GM graphics device.

dracayr

---

### Post by clhsharky on 2010-05-01
HI

I had issues with Ubuntu.32 kernels.
 I use OSS drivers so I'm not stuck with 2.6.32.xx kernels. 
I moved on to newer kernel 2.6.34.rc6, solved my problems.

Sharky

---

