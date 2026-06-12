---
title: "Installing Ubuntu on EeePC - Could not find kernel image"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by ConMan318 on 2010-02-11
I've been trying to install Ubuntu on a new EeePC, which doesn't have an optical drive so I am trying to install from USB.  I found a whole lot of guides that all seem to mix and match segments based on the method of install, and I have no clue what the right way is.  Some say you need to run an executable with the .iso file and put other files on there, some say that other files should be there, and some don't mention anything about that.

What I've done: I put the Ubuntu desktop 9.10 i386 iso file on an otherwise empty USB drive.  That's the only file in there.  I restarted the EeePC and got it to boot to the USB drive.  I get a black screen with the message:

```

Could not find kernel image: linux
boot:

```

Yes, I've searched for similar issues, and either they are referring to a different distribution, or are referring to instructions involving other files that are on the USB drive.  I would try putting other stuff on the USB drive but all the information seems conflicting.  This doesn't seem like it should be hard; if anyone has done this on an EeePC I would appreciate advice on what you did to make it work.

Do I need to run the pendrive linux executable on the .iso image?  Do I need to put other files on it?  How do I make it find the kernel?  It's very frustrating.

Thanks for any help :)

---ConMan

---

### Post by ConMan318 on 2010-02-11
Solved: Used [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) choosing 'disk image' radio button and navigating to downloaded .iso file and choosing USB drive location for destination.

<3

---

### Post by farsight on 2010-02-11
Hey conman,

How did you transfer the .iso to the USB stick? I believe there is an ubuntu program that allows you to correctly setup a USB drive as a bootable system (USB-creator - in synaptics package manager). 

Also, have you ensured the MD5 sum matches that provided when you downloaded the UNR 9.10 system?

Farsight

---

### Post by ConMan318 on 2010-02-11
Before this install I only had Windows on my desktop, so I put the .iso on the USB drive through Windows.  The MD5 did match, no errors.

---

