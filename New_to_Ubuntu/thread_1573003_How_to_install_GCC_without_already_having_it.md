---
title: "How to install GCC without already having it?"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by mcooley on 2010-09-12
I bought an ASUS eeepc that has a stunted version of ubuntu and tons of old software, including Firefox 2.0.  The internet is quickly disappearing from view because I'm unable to install newer versions of the supporting software without gcc. I can't install gcc because the system doesn't already have it. I can't even install syslinux so that I can create a bootable flash drive. The system does have cc1 but  'configure' doesn't want to use it. I tried making a symlink from /bin/cc1 to /bin/gcc but 'configure' doesn't like that either.

I'm completely stymied. This is  the only computer I presently have.

Here's the system...

/proc> cat version
Linux version 2.6.21.4-eeepc (root@i386-coreos) (gcc version 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)) #2 Tue Feb 19 11:46:29 EST 2008

I'm not a total newbie but I'm feeling awfully stupid. How do I get started so that I can either compile some new software or install to a bootable flash drive and bring this netbook out of the ice age?

Thanks,
Michael

---

### Post by abs_kkk on 2010-09-12
this looks similar to your problem

[http://ubuntuforums.org/showthread.php?t=120421](http://ubuntuforums.org/showthread.php?t=120421)

---

### Post by mowglinz on 2010-09-12
I have one of those. Ubuntu desktop installs well from a USB flash drive. Boot's slower but better overall. Must get around to trying the 10.04 Netbook edition.

---

### Post by coffeecat on 2010-09-12
> **mcooley said:**
> I bought an ASUS eeepc that has a stunted version  of ubuntu and tons of old software, including Firefox 2.0.

Are you sure that's a version of Ubuntu? That could be the version of  Xandros (another Linux distro) that came with the EeePC. Have a look at  the screenshots in this link:

[http://linuxhelp.blogspot.com/2008/01/asus-eeepc-consumer-friendly-laptop.html](http://linuxhelp.blogspot.com/2008/01/asus-eeepc-consumer-friendly-laptop.html)

Is that what you see? If so, you have the EeePC version of Xandros.  Another check. What does 'cat /etc/issue' from the terminal tell you?

If you do indeed have Xandros, then you are better off installing a  proper version of Ubuntu. In fact you are far better off. In my experience that version of Xandros was poor, and is probably no longer supported. The full Ubuntu (current version) desktop or netbook version  runs well enough on my EeePC 701.

However, if you do have something based on Ubuntu, it will be an old version if it has Firefox 2 and, if  I remember correctly, the 2.6.21 kernel  was the one that came in  Ubuntu 7.10, which is now unsupported. That is - no updates and software  available for it.

What is the model number of your EeePC?

**Edit:** just noticed this is in your post:

> Linux version 2.6.21.4-**eeepc**That's not an official Ubuntu kernel. That's either the Xandros kernel, or a kernel in one of a number of small-time enthusiast-created netbook distros that were created in the height of the netbook craze in 2008. I'd put my money on Xandros which no one here can help you with and which, believe me, you would be best getting rid of.

---

### Post by GregBrannon on 2010-09-12
> The internet is quickly disappearing from view . . .

It sounds like you HAVE the internet.  Why don't you use it to update the software you have, including the OS, rather than trying to compile a bunch of code to shore up an ancient OS with outdated software?

---

### Post by coffeecat on 2010-09-12
@mcooley, apologies, I should have added...

> **mcooley said:**
> How do I get started so that I can either compile some new software or install to a bootable flash drive and bring this netbook out of the ice age?

If you want to install a decent version of Linux - the current long-term support Ubuntu 10.04 would be what most here would recommend - you can install it to the internal SSD, replacing whatever prehistoric version of Linux you already have. If this is what you want to do, just post back and people can point you in the direction of suitable howtos and where you can get the ISO image for Ubuntu.

---

