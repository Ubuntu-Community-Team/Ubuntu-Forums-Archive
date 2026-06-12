---
title: "Question about creating your own DISTRO!"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by codfishy on 2009-01-17
Well, for some reason, I believe that different Linux Distros are just different layouts. That's it.
Believing that, I wonder, how do people get bugs, and "failures" if all that they are changing are layouts?
Is it that hard just to change the appearance of a certain Distro?

Of course, you need to download different programs, but it mustn't be that hard just to do that..

If there is more to it then just changing the appearance of it, please, let me know.

EDIT:  I'm using Reconstructor, by the way.  Well I'm in a bind between using Reconstructor and LFS(Linux From Scratch).

---

### Post by ibutho on 2009-01-17
Distros are not simply just different "layouts". They share similar features, but they also have a lot of different underlying technology and philosophies. For example kernels are not necessarily the same, xorg versions maybe different, packaging systems, configuration tools etc.

---

### Post by codfishy on 2009-01-17
> **ibutho said:**
> Distros are not simply just different "layouts". They share similar features, but they also have a lot of different underlying technology and philosophies. For example kernels are not necessarily the same, xorg versions maybe different, packaging systems, configuration tools etc.

Would it be possible to use Ubuntu as the base for my custom Distro, but make everything different so that it doesn't look exactly like Ubuntu?
I've been browsing on sites and I'm thinknig of changing everything around, and making an entire different distro out of it.

Is that possible?

---

### Post by Darkade on 2009-01-17
It's not just that. Different distros many times have different ways to manage binaries. Like Debian based use deb files, and others use RMP or others.

Also it has to do with the way you configure the distro. ARCHlinux is more similar to BSD in the sense that most of the important configurations are centralized in a single file /etc/rc.conf

If there are repositories then distributions are likely to manage the differently and with different apps, apt-get, Pacman, yum are some apps to do that.

Linux distros shere the Kernel, but that's the core of the OS. Configurations, and approaches to the end-user are different from distro to distro. Some are focused on beeing User-friendly, some in being simple, some to be easy to install, some are for desktops, some are for servers... in the world of linux one shoe doesn't fits all

---

### Post by Darkade on 2009-01-17
> **codfishy said:**
> Would it be possible to use Ubuntu as the base for my custom Distro, but make everything different so that it doesn't look exactly like Ubuntu?
I've been browsing on sites and I'm thinknig of changing everything around, and making an entire different distro out of it.

Is that possible?
And yep that's possible, you might want to check this link

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

It sure is a lot of work, but I think it's worth it

---

### Post by codfishy on 2009-01-17
> **Darkade said:**
> And yep that's possible, you might want to check this link

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

It sure is a lot of work, but I think it's worth it

Do you think it would be kind of a cheap way in creating my first distro.. if I use Reconstructor?

---

### Post by theozzlives on 2009-01-17
I can think of a couple of Distros  that use  Ubuntu as it's  base. A lesser  known  Pioneer  is one.

---

### Post by Darkade on 2009-01-17
> **codfishy said:**
> Do you think it would be kind of a cheap way in creating my first distro.. if I use Reconstructor?
I really haven't tested reconstructor, so I can't give you an opinion about that. However for what I've heard If you just want to add some visual tweaks, or add a couple of apps reconstructor might bee a nice option

---

### Post by codfishy on 2009-01-17
Actually, I've decided I'm going to go through the steps on here:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
;D

I'm going to do what I CAN do this entire weekend.. and see where that brings me.

---

### Post by Paqman on 2009-01-17
> **codfishy said:**
> Would it be possible to use Ubuntu as the base for my custom Distro, but make everything different so that it doesn't look exactly like Ubuntu?


Sure, there's quite a few Ubuntu-based distros already. Generally they change the default set of apps and may use a custom repo. Some have different artwork, some don't.

---

### Post by Darkade on 2009-01-17
> **codfishy said:**
> Actually, I've decided I'm going to go through the steps on here:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
;D

I'm going to do what I CAN do this entire weekend.. and see where that brings me.
Glad the link helped :D

---

### Post by utnubuuser on 2009-01-17
Hi -- There is a link on the gNewSense site for a distro builder as well.

Huge download though.

---

### Post by codfishy on 2009-01-17
> **Darkade said:**
> Glad the link helped :D

Honestly, I can't thank you enough.
I'm so excited to start it that I can't even sleep right now.
;(

---

### Post by codfishy on 2009-01-17
Would I also be able to create my own distro with this guide?
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

---

