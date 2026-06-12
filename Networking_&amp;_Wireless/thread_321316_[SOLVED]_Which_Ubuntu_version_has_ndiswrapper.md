---
title: "[SOLVED] Which Ubuntu version has ndiswrapper"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by pappo on 2006-12-18
Does any Ubuntu distribution (Xubunt, Kubuntu, Ubuntu, etc..) come with ndiswrapper pre-compiled in the kernel ?

---

### Post by stupidkid on 2006-12-18
You can't compile ndiswrapper into the kernel, but you can install it. I believe it's on the 6.06 (and probably 6.10) cd. Put the ubuntu cd into the cdrom and add the cdrom as a repository using Synaptic.

---

### Post by az on 2006-12-18
They all do.  

The ndiswrapper module is already part of the kernel that ships and you need the userspace tool to add your windows inf file - install ndiswrapper-utils.)

On any Ubuntu live cd, you can install ndiswrapper-utils by inserting the disk once you have booted to your ubuntu desktop - a repository is on the disk that is apart from the live session.  The package manager will start when the disk is inserted and you will be anle to install that package then.

Alternatively, you can add a cd as a repository using synaptic or by running

sudo apt-cdrom add

and then inserting the cd.

---

### Post by pappo on 2006-12-18
azz
Thanks.  I was able to install ndiswrapper-utils.
Now I am having problems with the "sudo modprobe ndiswrapper" command.  I get an error saying "invalid argument".  So I cannot add it to the kernel.

---

### Post by az on 2006-12-19
> **pappo said:**
> azz
Thanks.  I was able to install ndiswrapper-utils.
Now I am having problems with the "sudo modprobe ndiswrapper" command.  I get an error saying "invalid argument".  So I cannot add it to the kernel.

You have the wrong inf file or there is already a module loaded that is trying to use your card.  You need to blacklist the native linux module that is trying to make your card work, and then reboot, to be able to use ndiswrapper.  Also, you generally need to latest version of you inf file - the one that shipped with your card may be too old.

Check the changelogs on the ndiswrapper upstream site to see if your card is only supported by a version of ndiswrapper that is later that the one that ships with the version of Ubuntu you are using.  This is rarely the case, so you usually don't have to recompile ndiswrapper to get your card to work.

---

### Post by pappo on 2006-12-19
azz

Would you give me a URL to that "ndiswrapper upstream site"

---

### Post by pappo on 2006-12-19
Thanks for all the help.  I got my wireless pci card enabled.  I got ndiswrapper off the CD, and then discovered I was missing one ndiswrapper package.  I did not have ndiswrapper-utils-1.8 installed.
I am still having a few problems connecting, but that may be signal strength issues.
When I check using iwlist, it says my access point signal strength is 0/100 so I have to work on that.

---

### Post by az on 2006-12-19
> **pappo said:**
> azz

Would you give me a URL to that "ndiswrapper upstream site"


You need to check the changelogs from the releases after 1.8

Like this:
[http://sourceforge.net/project/shownotes.php?group_id=93482&release_id=468882](http://sourceforge.net/project/shownotes.php?group_id=93482&release_id=468882)

I think the tarball contains the complete list of changes.


For the current list of proper inf files:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

---

### Post by bxlinux on 2006-12-19
Is ndiswrapper only used for wireless cards? Can it be used for integrated ethernet cards?

---

### Post by az on 2006-12-19
> **bxlinux said:**
> Is ndiswrapper only used for wireless cards? 

[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

With ndiswrapper, virtually every miniPCI (builtin), PCI, PCMCIA (Cardbus only) or USB wireless network card works in Linux. Although ndiswrapper is intended for wireless network cards, other devices are known to work: e.g., USB to serial port device, ethernet card, home phone network device etc. See Wiki entry List for devices known to work.

wiki list:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

---

