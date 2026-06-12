---
title: "Installing on a Mac"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by HarrisonNapper on 2010-01-15
So I've recently started helping a friend install Ubuntu on a Mac. On an 80GB HDD, I have 20GB Ubuntu, 8GB swap (I'm aware that's unnecessarily large), and (for those not keeping up with the numbers) 52GB free space. Note that they're all in that order, so Mac is not "first" in the partition tables. When I put in the CD to install Leopard, it doesn't recognize any place to install OSX. In disk utility, it shows the disk, but will not/cannot modify the partition tables. So I used GParted Live, formatted the free space as HFS+ and got the same thing. I realize this would be better directed toward the Apple crowd, but this is where I'm used to hanging around and I thought others may have tried this. If I need to backup and re-install, will the OSX image backup be sufficient or will that not play well with Ubuntu?
 
Thanks so much in advance for any help you can provide.
 
Cheers.

---

### Post by alwayshere on 2010-01-15
you could try virtualbox
[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

to install it put below in terminal

sudo apt-get install virtualbox

---

### Post by HarrisonNapper on 2010-01-16
Hm, I've always heard that VB doesn't play well with OSX either as Guest or Host. However, I want to install the two OSes on separate partitions.

---

### Post by llamabr on 2010-01-16
As you say, that's too much swap.

Also, it's much easier to install osx first.  Back up your home dir, and start over.

[http://www.philroche.net/archives/osx-and-ubuntu-dual-boot/](http://www.philroche.net/archives/osx-and-ubuntu-dual-boot/)

---

### Post by Cowchip7 on 2010-01-16
Do you have an intel or a power pc?

---

### Post by scorp123 on 2010-01-16
> **HarrisonNapper said:**
> Hm, I've always heard that VB doesn't play well with OSX   Unless you can show me sources for this ... I have to call this BS. Because I use VirtualBox on my MacBook Pro. No problems whatsoever.

> **HarrisonNapper said:**
>  either as Guest or Host.   Sun Microsystems does not support illegal "hackint0sh" versions of Mac OS X on VirtualBox, yes. All those illegal "iPC", "iAKTOS", "Mac OS X86" disks will not work on any version of VirtualBox. But VirtualBox works tip top on OS X.

And if you're not so convinced about (free) VirtualBox you can still buy one of the commercial solutions that don't cost too much, e.g. Parallels or VMware Fusion.

---

### Post by HarrisonNapper on 2010-01-16
> Unless you can show me sources for this ... I have to call this BS. Because I use VirtualBox on my MacBook Pro. No problems whatsoever.

Was going off of memory. Works fine as a host. In either case, I run VB at home (for those times when I have to have Windows), so I'll look in to running Ubuntu inside of VB. Typically, I try to run it natively.

> As you say, that's too much swap.

Also, it's much easier to install osx first. Back up your home dir, and start over.

[http://www.philroche.net/archives/os...ntu-dual-boot/](http://www.philroche.net/archives/os...ntu-dual-boot/)

Thank you. This is most likely what I will do.

> Do you have an intel or a power pc?

I believe he's got an Intel, but I'm not there right now. Will check.

---

### Post by scorp123 on 2010-01-16
> **HarrisonNapper said:**
>  I believe he's got an Intel, but I'm not there right now. Will check. You could check with e.g. the "**uname -a**" terminal command ... that should spit out the CPU architecture similar to what you'd get from a Linux system.

If it's Intel it should respond with a string containing "i386" ... On a PowerPC system you'd probably get some string containing the letters "ppc".

---

### Post by HarrisonNapper on 2010-01-21
Sorry about the delay; it was an intel, but I'm just installing OSX and running Ubuntu through VB. Will the steps for setting up the mac keyboard/mouse in Ubuntu still be applicable within VB? Thanks everyone for all of your help, I'll be marking the thread as solved.

Cheers.

---

