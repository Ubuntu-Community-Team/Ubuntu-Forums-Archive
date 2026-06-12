---
title: "Question about dual boot/ubuntu updates"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by alliemack on 2009-04-24
Actually, I'm not sure what title to use for this question -- rather vague...

I've had many dual-boot systems in the past -- Windows XP + some form of Linux.  However, these were not of my own doing (my brother has been trying to teach me the way of Linux for years).  I don't mind any version of Linux, but have always struggled with dual boot issues and would wind up deleting his Linux-specific partitions (he does not live near me).

I'm not positive, but I seem to recall that the boot issues had something to do with certain features in Kubuntu (or whatever Linux form was installed) getting updated and messing up the boot loader (pardon my word usage -- not sure what to call some of these things).  It wouldn't have been a big deal if I'd known what file to edit and how to edit it (or what change to make depending on what actually happened...).

I just bought an Asus netbook and am going to attempt to teach myself some programming.  Per my brother's instructions, I created a couple of ext3 partitions and a swap partition -- in addition to a NTFS partition for Win XP.

I've already installed XP, but have not installed anything on the remaining partitions.  I've got a relatively current Ubuntu installation disk -- would it be relatively simple to install Ubuntu with a dual booting feature that would remain stable (i.e., updates would occur without making the boot loading process break)?  

I hope these questions make sense.  My brother is a programmer, and expects us all to embrace terminal commands.  I wouldn't mind if I actually knew a few... :)  

If it matters, I don't mind learning a few things -- I mainly need to either have something that will offer a dual boot menu pretty much without fail, or if something alters that process I need to know what to do to fix it.

Thanks very much.  alliemack

---

### Post by Didius Falco on 2009-04-24
You've already eased the way by installing Windows first. Ubuntu (most "flavors" of Linux, for that matter) are very polite about recognizing other operating systems.

For example, I'm currently quad booting: I have Win XP, 2 separate installs of Ubuntu 8.10 and a new install of 9.04, and each has simply added the previous ones to the Grub boot menu.

Here is a link to what I consider one of the best guides to the Grub bootloader around, for you to look over and familiarize your self with.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Now, on to your main question: Yes, it should go without a hitch.

Before you install, load the Live CD with the "make no changes" option and play around with it for awhile. If all your hardware works okay,  you are all set.

After you install, you'll first see the Grub menu, which will give you the option of booting into Ubuntu, booting into Ubuntu in Recovery mode, loading Memtest or loading windows.

The updating will occur from within Ubuntu, and any newer kernel versions will simply get added to the Grub menu.

If, at any time, you have trouble with booting, simply load the live cd up and you'll have access to the web, which greatly eases finding help with whatever problem you have.

The folks here are always happy to help, and the only dumb question is the one you didn't ask. <G>

You'll learn plenty of command line stuff as you go along, and you may be surprised how fun and fulfilling it turns out to be.

Have fun, and remember, help is always here.

---

### Post by alliemack on 2009-04-24
Thank you Didius Falco for your quick and informative reply.  That was a good tip about using the live CD -- I use them quite a bit when building machines and forget to even try them to get online.

---

