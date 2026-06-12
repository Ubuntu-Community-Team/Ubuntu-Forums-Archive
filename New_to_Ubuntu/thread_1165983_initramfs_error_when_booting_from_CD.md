---
title: "initramfs error when booting from CD"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Wayne Twine on 2009-05-21
HI
 
I am an absolute beginner with an installation prolem, so wasn't sure which forum to post this on.
 
Anyway, I want to try out Ubuntu on my PC.  I downloaded the .iso for jaunty and burnt an image onto CD.  After inserting CD and rebooting, I get to the Ubuntu screen with the boot options.  I select "Try Ubuntu with no changes ...etc" and hit enter.  The next screen with the Ubuntu logo appears, and then a screen appears saying "Loading, please wait" and "(initramfs)".  Nothing happens and the screen eventually goes blank.  
 
I have tried interventions suggested on some threats, like hitting F6 and adding "all_generic_ide', but to no avail.
 
My machine has 2  hard drives, 110 GB each (boots from c, d is for data), 1 GB RAM and nvidia GeoForce graphics card, if that helps.  I'm running Windows XP.
 
Please help, as I've been like a kid on Christmas eve, and now I can't get the damn present open!! :-)
 
Cheers

---

### Post by X181 on 2009-05-21
I am also an absolute beginner, so i cant help you directly with your problem, but did you try different versions of the live-cd (8.04, 9.04)? Perhaps your cd is defect. This would help to locate your problem...

---

### Post by superprash2003 on 2009-05-21
check your CD for errors, you should get that option in the beginning, try burning another one in slow speed..

---

### Post by Wayne Twine on 2009-05-22
You may be onto something.  I reburnt the iso image at a slower speed (2x) and rebooted with the CD.  First time I got the same error message again, but when I tried again, this time making changes such as selecting noapic and nolapic, as well as replacing quiet splash with all_generic_ide (as I did yesterday) it actually started loading, which it did not do yesterday.  However, alas, it bombed out again with the initramfs error at [    3.977469 USB etc etc].
 
So we seem to be getting closer, but not there yet.  I am going to try to burn to a totally new CD....

---

### Post by Wayne Twine on 2009-05-22
Nope.  New Cd, same problem.  Tried on another machine and managed to boot so must be an incapatibility with my settings.   Any ideas?

---

### Post by clive littlewood on 2009-05-22
Hi Wayne

Welcome to Ubuntu Land

I would suggest that you try the "Alternate CD" download from Ubuntu.com

I am thinking you may have a graphics card problem and the Alternate CD uses a non graphical to load the OS.

If you give this a try come back and let us know how you go on.

Clive

---

### Post by Wayne Twine on 2009-05-22
Thanks Clive
 
Unfortunately, my internet connection is very slow so it takes about 8 hours to download 700 MB!!  I'm loath to do this again if there is another way to try to tackle the graphics card issue.  If not, I'll bite the bullet and download the alternate cd.
 
W

---

### Post by clive littlewood on 2009-05-22
Hi

To solve any issues is easy, once you get the system up and running !!

I think it is worth biting the bullet and going for the alternate download.

Perhaps use a torrent and leave it to download overnight !!!

Somebody will be here ready to help you      :D

Clive

---

### Post by Wayne Twine on 2009-05-22
Okey dokey.  I'll give it a try and post feedback on the result of the reboot using the Alternate download.
 
Cheers

---

### Post by Wayne Twine on 2009-05-27
Problem sorted!  

It turns out that the CD-ROM drive I was installing from was set as slave.  The master CD-ROM drive has been giving trouble, so I don't use it.  When I switched slave to master and vice versa by changing the pins at the back of the drives, I managed to install hassle free.

Same issue caused "CD-ROM couldn't be mounted" error when I tried to install from the Alternate CD on the slave drive.


I hope that helps others with similar errors at installation.

---

### Post by clive littlewood on 2009-05-27
Hi

Glad you sorted it and thanks for giving your solution as it might promt others to see if they have the same problem.       :D

Regards

Clive

---

