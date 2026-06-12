---
title: "Pen Drive Boot"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by Faud on 2009-08-13
Hello,

I have put Ubuntu on a 4 gig flash drive following the instructions from pendrivelinux.com

When I load it up I get the normal Ubuntu start up screen and then I get a screen full of

end request i/o error dev fd0 sector0
buffer i/o error on device fd0 logical block 0

After a screen of this it tells me that it is loading drivers and then pops up Ubuntu.  I can use gimp/browse the web etc.  I am wondering if that error stuff is normal though, also if I run ubuntu perstintaly does this mean that I can download graphics drivers and use them or do updates to the system?  Or do I need to keep everything just as it installed on the pen drive orignally?

Thanks

---

### Post by verbal.kint on 2009-08-13
Fd0 is a floppy drive from what I can see, is there a floppy drive on your machine?

[http://www.linuxquestions.org/questions/linux-software-2/linux-kernel-endrequest-io-error-dev-fd0-sector-0-319629/](http://www.linuxquestions.org/questions/linux-software-2/linux-kernel-endrequest-io-error-dev-fd0-sector-0-319629/)

With regards the updates, you should be able to run and install updates as long as there is still room on your pen drive.

---

### Post by Faud on 2009-08-13
Well I am booting from a USB stick but as far as my boot order thinks, my usb stick is a hard drive

It will give me something to ponder about at work today I suppose.

---

### Post by Hospadar on 2009-08-13
I would say if it works, don't worry.

A lot of times mysterious and non-important error messages come from hardware that maybe doesn't totally conform to a standard, or minorly broken in some way, or not totally supported.  Generally I'd say don't worry about things until they cause trouble. (but do keep them in mind if you have other mystery problems)

---

