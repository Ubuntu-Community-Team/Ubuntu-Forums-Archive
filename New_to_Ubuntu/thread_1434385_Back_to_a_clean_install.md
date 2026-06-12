---
title: "Back to a clean install"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by Twizzle on 2010-03-20
Is it possible to uninstall all software and revert to a 'clean' install without actually doing a new install?

I have Ubuntu Server Edition 9.10 x64 on a home server and have been messing around trying to get Zoneminder to install. I have tried a number of 'walk throughs' but with no luck and I assume that I now have a number of settings / programs that may be interferring with each other and causing just as many problems!

I would like to start again from scratch but have alot of data stored on the hard drives that I don't really want to loose. 

Is there a way to tell Ubuntu to clean itself as such and remove all third party applications / programs?

The problem with doing a fresh install and keeping my /home intact is that I do not have a spare IDE port on the motherboard and only have an IDE DVD drive. I installed, added a further IDE HDD and added to the LVM partition. As a result, for me to re install, I would have to split the LVM partition and loose data from it.

I did initially look at using a USB stick to try and install from but it would not work - my motherboard apparently allows booting from a USB but would not recognise an Ubuntu installation drive.

I have seen a similar question posted with a negative response (I think the answer was not unless you cloned after install) but was wondering if tings had moved on since then as the post was a good few years old.

---

### Post by yeats on 2010-03-20
> Is it possible to uninstall all software and revert to a 'clean' install without actually doing a new install?

There's not a way to automatically do this.  To "revert" you would have to retrace your steps on every change you've made, and if you're compiling things from source, that makes it even less possible.

> I would like to start again from scratch but have alot of data stored on the hard drives that I don't really want to loose.

This is a good time to think out a backup strategy, probably to an external hard drive.  If you move your data off, you can then do a fresh install with a separate /home partition, which will ease this situation in the future.

Good luck!

---

