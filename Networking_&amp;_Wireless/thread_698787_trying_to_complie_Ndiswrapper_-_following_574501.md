---
title: "trying to complie Ndiswrapper - following 574501"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by paries on 2008-02-16
hello, i am follow the thread
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
to build Ndiswrapper 

the first thing in the INSTALL is the Prerequisites
they suggest this.
 ls /lib/modules/`uname -r`/build

I get
# ls /lib/modules/`uname -r`/build
ls: /lib/modules/2.6.22-14-386/build: No such file or directory

When i do
apt-cache search 'kernel' | grep linux | grep source
I get :
linux-source - Linux kernel source with Ubuntu patches
ketchup - update utility for linux-kernel sources
linux-wlan-ng-source - linux-wlan-ng driver
linux-source-2.6.22 - Linux kernel source for version 2.6.22 with Ubuntu patches

So what am I missing here?

thanks
randy

---

### Post by paries on 2008-02-16
Fixed this one

I needed to do this

aptitude install linux-headers-2.6.22-14-386

---

