---
title: "specific questions for live cd building procedure"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by MichaelBurns on 2010-02-27
I am trying to make my way through the procedure for building a live cd from scratch.  Of course, there are various places to find instructions.  I will focus on the set of instructions found on this page:  [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch).

I have two goals:  (1) to get through the procedure and come out with a working flash drive, and (2) to understand everything that I have done.  I don't think that I need help with (1); I think that's just a matter of trial and error.  On the other hand, (2) is where I hope you will come in.  So, to get started:

debootstrap is basically the very first thing to do, but it does so much that I already feel left out of the entire procedure.  It looks like it just creates a directory structure, but it apparently also installs binaries.  Different webpages give different options.  For example, some webpages give --arch=i386 while others don't, and some give the name of some deb repository while others don't.

The webpage says that the chroot environment doesn't need a kernel.  But then, how would I be able to run commands in the chroot environment?  I thought that the binaries that execute the commands need to do so in the context of a kernel.  And the whole point of the chroot environment is to prevent access to anything that is installed on the host system outside of it.

The webpage mentions that, if I want to use the desktop-base, then I need to bind the /dev in the chroot environment to the /dev in the host environment.  This is to be implemented with the bind option of the mount command.  I am confused by this, because my understanding of /dev is that it is specific to my computer, but the procedure is supposed to build an installation that works on other computers.  So, shouldn't the installation that I build automatically do this binding?

---

### Post by yeats on 2010-02-27
> debootstrap is basically the very first thing to do, but it does so much that I already feel left out of the entire procedure. It looks like it just creates a directory structure, but it apparently also installs binaries. Different webpages give different options. For example, some webpages give --arch=i386 while others don't, and some give the name of some deb repository while others don't.

debootstrap creates a new Linux filesystem that is self-contained and can be chroot-ed into to run commands on - basically allowing you to tailor your own version of (Ubuntu) Linux.  Regarding the options, have you read the debootsrap man page?

> The webpage says that the chroot environment doesn't need a kernel. But then, how would I be able to run commands in the chroot environment? I thought that the binaries that execute the commands need to do so in the context of a kernel.

The chroot environment uses your existing kernel, just as a Live CD itself loads a kernel to then install a new version of Linux on your hard drive.

> And the whole point of the chroot environment is to prevent access to anything that is installed on the host system outside of it.

This is true in the sense that any changes you make to the new filesystem (software installation, etc.) do not affect your host system.  It does, however, make use of your host's kernel.

---

### Post by MichaelBurns on 2010-02-28
Thanks, chrissharp!  Affirmation is better than nothing.

> **MichaelBurns said:**
> I don't think that I need help with (1); I think that's just a matter of trial and error.Actually, I am probably wrong about the above statement.

> **chrissharp123 said:**
> Regarding the options, have you read the debootsrap man page?Yes, but it's not very informative.  The meaning of the options are not what confuses me (i386 is pretty obvious, for instance), just what *exactly* is debootstrap doing.  Actually, I think I am on my way to answering this question (chapters 1-5 of [these instructions]("http://www.linuxfromscratch.org/lfs/view/6.5/")), and the answer seems to be "Holy crap!"  However, as I run into problems, I am wondering if debootstrap really does all of that.  I made sure to download the one for karmic, and then dpkg it, so I don't suspect that I'm using the wrong version.

> **chrissharp123 said:**
> The chroot environment uses your existing kernel, just as a Live CD itself loads a kernel to then install a new version of Linux on your hard drive.That still confuses me.  In particular, I want to build karmic, but I'm running jaunty.  Doesn't that require a different kernel in the chroot environment (2.6.31) compared to my host jaunty environment (2.6.28 )?  Not that I know anything whatsoever what this means.  I am only guessing that means something about some binaries that drive some hardware.  But even I can compare two numbers and tell you that they're different, and I don't want to leave any loose ends.

FYI:

If you copy your "/etc/apt/sources.list" into a chroot filesystem in which you will build a different release, then make sure to edit the name of the release to the appropriate name everywhere in the "sources.list" file (in the chroot filesystem; not your host filesystem).  For example, suppose that you are running jaunty, and you want to build karmic in your chroot environment.  Copy your jaunty "sources.list" file into the chroot filesystem, and then everywhere in this copy, replace "jaunty" with "karmic".  This is something that the instructions on [this webpage]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch") neglect to mention.

---

### Post by MichaelBurns on 2010-03-01
What is the purpose of a "README.diskdefines" file?

I can just copy the contents of the one given on [the webpage]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch"), but this may only work if I am building karmic, and anyway I would like to understand what I'm doing.  I have no idea what are the "#define" variables being used for.  A google search has not revealed any useful information about this.

---

### Post by MichaelBurns on 2010-03-21
I don't know if I successfully completed the procedure.  I finished without any errors, but I also made a few changes to the procedure in order to do that.  Unfortunately, I am unable to check if the usb stick works, because my laptop cannot boot from usb.

---

