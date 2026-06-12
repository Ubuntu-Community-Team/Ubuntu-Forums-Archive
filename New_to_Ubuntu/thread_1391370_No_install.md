---
title: "No install"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by rosswmcgee on 2010-01-26
I was trying to help a friend by installing 9.10 on an older computer with

xp on it. Ubuntu 9.10 stalled at 53%, Xbuntu stalled at 24%,puppy linux 

runs only on the live cd but would not install to HD, Fedora stalled at about 60%. I used the entire Hd selection for the install so windows is 
gone. I spent two days on this. I give up and will give the computer to 
some one else to try it. Any ideas?

---

### Post by Rocket2DMn on 2010-01-26
Sounds like there may be a problem with the HD itself.  Since you aren't trying to dual boot, you can use the LiveCD to first format the disk (preferably ext4).  Then use fsck to check the filesystem for errors.  Karmic also comes with a utility that should automatically see if the disk is reporting errors - I thought it ran by default on the LiveCD, but I could be wrong.

---

### Post by adam814 on 2010-01-26
Honestly the most common reason I've seen an OS fail to install repeatedly is hard disk failure.  The first thing I would do would be to run the HD manufacturer diagnostic on it.  Or at the very least with the LiveCD you could go to System > Administration > Disk Utility and check the S.M.A.R.T. data on it

If that's not the case it could be that you need some particular kernel option to get the install to work.  Or you might need to tweak a setting or two in the BIOS (legacy mode for your SATA controller perhaps?).

---

### Post by rosswmcgee on 2010-01-26
This computer was a hand built job not a normal computer mfg.. I could not get as far

as live cd with it. Thanks! I am forwarding your replies to the next person that is going to give it a try.

---

### Post by oldos2er on 2010-01-26
What are this system's specs?

---

### Post by rosswmcgee on 2010-01-28
OK bottom line I gave the computer to another friend and after two days he was able to re-format the hard drive and install puppy linux. Since the user is a total comouter newbie, we will install ubuntu after he get used to googling and the use of a computer. Team work is what linux is all about. Thanks everyone.

---

### Post by Puppyite on 2010-01-28
Hi Ross,

I am author of [Puppy Linux FAQ](http://www.puppylinuxfaq.org/) the definitive guide for using and enjoying Puppy Linux. Please invite your friend to visit my site. There is no easier way to get started with Linux than by visiting [www.puppylinuxfaq.org](www.puppylinuxfaq.org)

Regards,
Puppyite

---

### Post by zipperback on 2010-01-28
If your system is dying during the initial install, it might be that you have a problem with bad media.

Boot the livecd and use the check media option from menu.

That should let us know if it's a media problem.

- zipperback
:popcorn:

---

### Post by Miljet on 2010-01-28
> If your system is dying during the initial install, it might be that you have a problem with bad media.
Three different operating systems, I seriously doubt it.

---

