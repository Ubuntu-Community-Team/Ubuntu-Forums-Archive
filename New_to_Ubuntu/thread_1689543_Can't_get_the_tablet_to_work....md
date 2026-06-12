---
title: "Can't get the tablet to work..."
date: 2011-02-16
forum: New to Ubuntu
---

### Post by f1337w00d on 2011-02-16
I've just made the switch to Ubuntu 10.10 on my Gateway M285, and I can't get the pen to work. I tried following the instructions here: [http://www.linlap.com/wiki/gateway+m285](http://www.linlap.com/wiki/gateway+m285), but to no avail. I checked, and it is not a wacom tablet (I know there is plenty of support for them elsewhere on the forum). 

I couldn't find xorg.conf at first, and when I finally found it through the terminal, it was blank.

I have tried finding help on google, but I couldn't find anything noob enough for me to understand.

Please help?

---

### Post by Favux on 2011-02-17
Hi f1337w00d,

Welcome to Ubuntu forums!

I believe the driver you want is fpit, packaged as xserver-xorg-input-fpit.  Check in Synaptic Package Manager and see if it is there and will install.  Plus now you can google fpit to do research.

From this Launchpad bug report:  [https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/565540](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/565540)

It looks like two things were/are going on.  The major one is someone reversed a critical X & Y in the code, but that's been fixed.  The other is that it hasn't been packaged correctly.  But from what it is saying you should be able to get it working in Lucid anyway.

Here's a couple of old (obsolete) threads on installing it:
[http://ubuntuforums.org/showthread.php?t=429701](http://ubuntuforums.org/showthread.php?t=429701)
[http://ubuntuforums.org/showthread.php?t=942109](http://ubuntuforums.org/showthread.php?t=942109)

Notice it is a serial device on a serial port /ttyS0.

---

### Post by f1337w00d on 2011-02-17
.

---

### Post by f1337w00d on 2011-02-17
That driver definitely seems like the right one, but when I try to get Synaptic to install it, it won't let me. It wants to remove the following drivers:
ubuntu-desktop
xorg
xserver-xorg
xserver-xorg-core
and a bunch of other xserver-input drivers

I'm assuming this is a bad thing; is there a way to install the fpit driver without removing all those other files while still making sure I have all necessary packages? Also, I'm not sure what you mean by "get it working in Lucid..."

And thanks for the help, I really appreciate it!

---

### Post by Favux on 2011-02-18
Hi f1337w00d,

You definitely don't want to let it install those packages.  So it's looking like the fpit package is seeing a version conflict.  Probably sees the packages it wants to remove as too new?  So it isn't packaged right or the driver hasn't been updated to run on X server 1.9 (Maverick).

What I was saying is the bug report links to a package (ppa?) that does work on Lucid's X server 1.7, at least for some.  But it looks like the last time fpit was supported for sure was X server 1.6 (Karmic).

Somewhere out there (in a blog?) someone may have figured out how to get it to run on Maverick.

I read somewhere Xorg was going to drop some driver support.  I don't know if fpit was among them, so I probably shouldn't mention it.

One thing to do is read the bug report carefully and see if you can do anything with it.  And then post on the bug report to keep it alive.

---

### Post by f1337w00d on 2011-02-18
Thanks for all the help, I'll update you if I'm able to find a solution.

---

