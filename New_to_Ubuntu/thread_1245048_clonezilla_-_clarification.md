---
title: "clonezilla - clarification"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by longtom on 2009-08-20
Hi,

I am somewhat hesitant and fear this will be just another thread nobody can help - but I will never die wondering...

After my somewhat disappointing sting with [remastersys](http://ubuntuforums.org/search.php?searchid=63183407), where I ran into trouble which nobody could assist me with, I decided to look around for alternatives.
Clonezilla kept appearing wherever I looked.

After having a look at there website and reading through the thorough and easy to follow [step by step instructions](http://clonezilla.org/clonezilla-live/doc/) and flipping through old posts in this forum, I still couldn't find an answer to the most important questions as far as I am concerned:

Once I have followed the step by step instructions, will I be able to use the iso file to reinstall my installation on a different PC with different specs?

In other words:

Will clonezilla provide me with a dvd, which I can pop in any healthy PC and install the setup as far as I am using it (desktop, programs installed etc)?

What will happen if the hd is a different size or make or both?

What will happen if the receiver PC has a different video setup?

Is it possible to clone only partitions (ie my 8.04 partition) and reinstall it on some other PC with a dvd with an iso file on it?

Any suggestions welcome.

---

### Post by jerrrys on 2009-08-20
[post not working  :(]("http://clonezilla.org/wiki/")

for some reason i cannot post this link so here's a screenshot

[ATTACH]125588[/ATTACH]
[ ]("http://clonezilla.org/wiki/")

---

### Post by longtom on 2009-08-20
Thanks for the image.  I, however, don't want it to save on a rewritable DVD.

My basic question is:

Can I backup my system in such a way so I can reproduce it on a different PC? *sigh

---

### Post by Aearenda on 2009-08-20
I use Clonezilla via a DRBL server to copy partitions via the server, so my use of it doesn't quite match. However, here is my take on the answers you seek:

> Once I have followed the step by step instructions, will I be able to use the iso file to reinstall my installation on a different PC with different specs?
The image Clonezilla makes isn't an iso file (although I gather it can make an ISO that you can burn afterwards that contains the image files). The partition image can be restored to any partition that is equal or larger in size. After that, tolerance of different hardware varies by operating system - Linux is much more forgiving of differences than Windows, for example, but you still need to know what to adjust - eg machine name, removing the memory of what network cards have been seen before, and the partition info in places like /etc/fstab and /boot/grub/menu.lst; you won't succeed in getting a 64-bit OS to restore onto a 32-bit machine :-). And of course, who knows what other odd things are going to happen? It wouldn't be an easily supportable installation, and I don't recommend doing any of this unless you are confident of your own diagnostic abilities.

> In other words:
Will clonezilla provide me with a dvd, which I can pop in any healthy PC and install the setup as far as I am using it (desktop, programs installed etc)?
It won't do that automatically, you'll need to adjust things.


> What will happen if the hd is a different size or make or both?I've had no troubles of this sort, but I'm not using radically different drives - I haven't tried restoring an IDE drive image to a SATA drive. Of course, you can't restore an image to a partition smaller than the original (so build your master system using small partitions).

> What will happen if the receiver PC has a different video setup?Linux will generally cope with this if the video hardware uses open source drivers, though you may need to install proprietary drivers in other cases.

> Is it possible to clone only partitions (ie my 8.04 partition) and reinstall it on some other PC with a dvd with an iso file on it?Yes to the first part - Clonezilla takes each partition separately, and you can select which one if it is not to take them all; but no to the second part, since it doesn't produce iso images on the DVD. You can burn the image files it does produce onto a DVD though, so in principle, you can achieve the same end result, though as I said above, it's not going to happen automatically.

---

### Post by mapes12 on 2009-08-20
Hello longtom

> Once I have followed the step by step instructions, will I be able to use the iso file to reinstall my installation on a different PC with different specs?

In other words:

Will clonezilla provide me with a dvd, which I can pop in any healthy PC and install the setup as far as I am using it (desktop, programs installed etc)?

What will happen if the hd is a different size or make or both?

What will happen if the receiver PC has a different video setup?If clonezilla works like partimage the answer is yes yes and yes. I took an image file of "/" i.e. the Filesystem on the first partition of my HP tc210 base unit and installed the image onto the first partition of my Dell Dimensions XPS T700r base unit. They have completely different hardward and different size HDD's. After the install I booted up and everything worked perfectly. From what I understand the reason for the compatibility is:

1. Partimage only copies used space / data. It doesn't copy across unused blocks on the HDD.
2. Unlike windoze which requires drivers to be installed for certain hardware, the Linux Kernel has a comprehensive open source driver database already compiled within the kernel.

I tried the same test with an image of an XP installation. It worked but was very buggy. Not a configuration you could rely on to work with.

---

### Post by longtom on 2009-08-20
Thank you for all the answers so far.  It's not a walk in the park and it appears a lot can go wrong....

---

### Post by Aearenda on 2009-08-20
> It's not a walk in the park and it appears a lot can go wrong....Yep - but having said that, if the hardware is similar, it does work for me :-).

Edit: BTW, Clonezilla uses Partimage for Linux partitions, and NTFSclone for NTFS. It can also use dd if all else fails, but that copies empty space too.

---

### Post by bwitherell on 2009-08-26
Clonezilla is great for cloning base images used for deployment. I use it as an alternative to Symantec Ghost. Although I have only used it for Windows deployments. I think your question is more about how Ubuntu deals with being cloned to different hardware rather than how clonezilla restores images onto different hardware.

The cloning software you use does not really have any affect on weather or not your image will be compatible on one PC or another.

The real limiting factors are:
-The OS you are cloning
-How the hardware differs between the PC the image was taken on and the PC receiving the image.
-How your OS deals with being cloned to different hardware

With clonezilla you can clone whole disks or partitions. It is up to you. You choose either one on the menu when you go to make your image.

Here is a link to a thread about how Linux deals with being cloned to different hardware. [http://www.linuxforums.org/forum/installation/123793-fast-image-deployment.html]("http://www.linuxforums.org/forum/installation/123793-fast-image-deployment.html")

Please post the results of your efforts. If you have any more questions about clonezilla please post those as well.

Thanks,
Brad

---

### Post by LewRockwell on 2009-08-26
the brief, safe, and simplistic answer to your question is NO.

if you create a bit by bit clone correctly, then that clone will obviously work in place of the original that the clone was cloned from

if you create a bit by bit clone correctly, then that clone will work on a different machine with EXACTLY THE SAME HARDWARE

if you create a bit by bit clone correctly, it MIGHT work with different hardware...or it might just APPEAR to be working correctly...until it doesn't...

and then...whoever does this...will come to the forums asking why their operating system broke...when it has been broken from the beginning since it wasn't installed originally on that machine

so again, for what you want to do(carry around an Ubuntu operating system clone that will work with varying hardware)...

NO

.

---

### Post by longtom on 2009-09-01
Thank you again for all your answers.

I think LewRockwell says it loud and clear:  For what I intend  to use CloneZilla it is not the tool to use.

---

### Post by slakkie on 2009-09-01
[https://help.ubuntu.com/8.04/installation-guide/i386/appendix-preseed.html](https://help.ubuntu.com/8.04/installation-guide/i386/appendix-preseed.html)

---

### Post by longtom on 2009-09-03
> **slakkie said:**
> [https://help.ubuntu.com/8.04/installation-guide/i386/appendix-preseed.html](https://help.ubuntu.com/8.04/installation-guide/i386/appendix-preseed.html)

Ufff....thanks

---

