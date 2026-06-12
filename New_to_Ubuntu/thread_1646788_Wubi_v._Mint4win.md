---
title: "Wubi v. Mint4win"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by degarb on 2010-12-16
Since running a package fix in recover console mode, destroyed my Wubi installation--unconfiguring the location of /root etc.   And no way to repair the installation, I can see.   Looks like a 6th wipe and reinstall wubi.  (grub2 wont install on my external drive, even with cd)

It took 4 hours to download 200 meg of updates, only to have it choke on a bad python 2 minimal replacement archive.  And no way to back out.  I read that mint is simply Ubuntu + a few preinstalled codecs.  Lord, I hate trying to get the codecs working in the browsers on Ubuntu. (one package doesn't work, and another by same name won't.) SO, I was thinking maybe mint4win would save me a few hours, wrinkles, and hairs.

But, will I not be able to get support.  Support is 100 percent of a programming language or OS install, since, any one unsurmountable roadblock will void its usage.

Also, is it 3 versions behind?

---

### Post by indytim on 2010-12-16
> But, will I not be able to get support. Support is 100 percent of a programming language or OS install, since, any one unsurmountable roadblock will void its usage.


Perchance, did you try the MINT support (as in forums, chat etc.)?
(You're currently in the Ubuntu forums asking questions about Mint...).

> Also, is it 3 versions behind?

To your question, NO.  The Mint Gnome version number is basically Ubuntu -1.  There is a conversion table buried in the Mints site which shows the effective Ubuntu equivalent. I'm at work now and not accessible to a lot of my links.

IndyTim / DataMan

---

### Post by ajgreeny on 2010-12-16
Why won't grub2 install on your external drive?

What is the exact error that you get when trying to install grub there?

Fix that problem and you may have a better way to go ahead.  Mint4Win is just about the same as wubi as far as I can make out, though I have used either, so may be the wrong person to answer the question best.

As to the versions, Mint 10 (Julia) is ubuntu 10.10 (Maverick), Mint 9 (Isadora) is ubuntu 10.04 (Lucid), and so on backwards.  Mint usually appears about 4 -6 weeks later than the equivalent version of Ubuntu, but otherwise you will probably get just about all the important support you need for Mint from this site, as well as [Mint Forum]("http://linuxmint.com/forum/index.php")

---

### Post by degarb on 2010-12-16
> **ajgreeny said:**
> Why won't grub2 install on your external drive?

What is the exact error that you get when trying to install grub there?

Fix that problem and you may have a better way to go ahead.  Mint4Win is just about the same as wubi as far as I can make out, though I have used either, so may be the wrong person to answer the question best.

As to the versions, Mint 10 (Julia) is ubuntu 10.10 (Maverick), Mint 9 (Isadora) is ubuntu 10.04 (Lucid), and so on backwards.  Mint usually appears about 4 -6 weeks later than the equivalent version of Ubuntu, but otherwise you will probably get just about all the important support you need for Mint from this site, as well as [Mint Forum]("http://linuxmint.com/forum/index.php")

Haven't tried mint yet, until a few minutes ago.  But I signed up for their forum last night.  After a couple hours of trying to load the register page.  Similarly, the forums were inaccessible all last night, and got in earlier, but cut off now.   

The ubu installer fails to load grub on external drive.  Just says it cannot be done.  I loaded live cd and manually added it. 

Looks like the Mint4win has same flaw as wubi: I cannot get updater to work since some missing dependency in python causes the updater to fail on 'unpacking python-minimal replacement'

Looks like I will have to stick with windows, since no one understands the nature of the python minimal replace freeze with no timeout. ;-(

---

### Post by sydbat on 2010-12-16
Just out of curiosity, have you tried doing a full dual boot install? That might eliminate all your problems.

---

### Post by thatguruguy on 2010-12-16
> **degarb said:**
> 
Looks like I will have to stick with windows

Considering all the problems you've had, that's probably the best idea.  Use what works for you. Linux isn't for everybody.

---

### Post by degarb on 2010-12-16
> **sydbat said:**
> Just out of curiosity, have you tried doing a full dual boot install? That might eliminate all your problems.

Well old machine.  I cannot boot into linux by adding grub in the external 500 gig drive, because of the bios.   If I put the grub in primary master, I am told the machine wont boot, even to windows, when I take the 500 gig dive off for what ever reason.

No one apparently knows how to use grub4dos to ditch grub2.  And installing grub to own partition, I haven't found directions on web yet, just blather discussing nature of grub. 

I suppose I have a gig or three available on primary master.  Can I use that to install Ubuntu, but use external drive for swap and home and bin.  Then if external drive is gone or arranged along side a second exteral drive, I can boot to windows, just not linux.

---

