---
title: "Why are you tagging on UUID?????"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by skypuppy on 2011-05-12
Tried to "upgrade" from 10.10 to 11.4 'seamlessly.'  Hah.  Took over 14 hours on high speed cable Internet with six core processor and still failed upon boot of 11.4.

Looks like it tried to boot from a specific UUID drive!  Why in the heck do you guys do that???  This isn't an OS that CAN be keyed to a particular drive because hard drives are THE most common failure point in PC's. What were you guys thinking?  Please stop this.

I had all the drivers loaded for my particular hardware in 10.10 but upgrading is always a Good Thing (R), right?  Of course, it didn't work and now I don't know which way to go or what to do.  Is my previous "download" directory still in place?  Are my drivers still able to be installed from there?  Lord have mercy.

Skypuppy
aka David

---

### Post by mcduck on 2011-05-12
Because UUIDs are the only reliable and automatic way to point to a certain partition. Labels work almost as well, but require human interaction to choose a suitable label (creating one randomly would be exactly the same as using UUID) and pointing to device names isn't reliable on some hardware.

Anyway, a mere upgrade would not have formatted your partition, so it's UUID wouldn't have changed. If you can give more details on what exactly you did it might be possible to figure out what went wrong, but the use of UUIDs sure isn't the problem. :)

(and *of course* Ubuntu is an OS that can be keyed to a particular drive/partiton, *every* OS is. The OS will always depend on the drive where it's installed. If that drive fails you'll have to make a new install anyway, so it makes absolutely no difference where the old install pointed to, and whether it did that by using UUID or some other method.)

---

### Post by skypuppy on 2011-05-12
11.4 gets to initramfs and dies.  I can do the minishell commands in text mode but cannot actually boot.  "Busybox" came in there somewhere.

UUID's are bad, bad news for many reasons.  For the most common, when your hard drive dies you can sometimes copy your system to a new disk if you don't have to deal with UUID's.  Another common situation is needing a larger disk.  Using qparted or similar tool to move a complete disk filesystem to a new disk appears to be quite problematic when hardcoded UUID's are involved.

I've been doing system work on computers since the late 1970's and this is the first time I've seen hardcoded UUID's on PC's that weren't locked systems like some Suns, some Norton stuff back in the early days, SGI boxes, and high dollar dedicated systems that ran on ordinary pc hardware.

I've never had a problem with using /dev/sda or /dev/sda3 or /dev/hda1 (for examples) when dealing with broken disks.  No hard links, please.  Also, I've never had to do manual input when dealing with soft links versus hardcoded UUID's (or CPU ID's or any other hardware specific copy protection madness methods.)

I have spent scores of hours getting 10.10 to where I wanted it, with uncommon hardware specific drivers and etc.  "Upgrading" to 11.4 promised to be painless, versus wiping the disks and clean intalls then redoing the SAME scores of hours AGAIN just because of an "upgraded" part of an OS.

---

### Post by mcduck on 2011-05-13
Well, good for you if you've never used a machine that doesn't change the hard drive's device names randomly on boot or if you happen to have a removable USB drive connected or not. Still, as long as such things happen, the UUIDs really are the only way to go.

Besides, it's not hard-coded. Really. It takes less than 5 minutes to change the few config files that reference to a drive's UUID. (or if you want to do it the other way, a single command to set the UUID to whatever you want).

I'd rather take 5 minutes of extra work in case a hard drive happens to die than a bunch of computers that can't actually boot reliably.

...and like I said, your problems are caused by something else than the use of UUIDs. If you did a normal upgrade, that wouldn't have changed any filesystem, and thus the UUIDS would still be the same. It only changes if you format or edit a partition.

Besides, if you some day happen to clone a broken root drive into another drive, the clone will have exactly the same UUID. So you don't even need to change anything, all setting file swill point to correct UUID.

Anyway, you still haven't told what exactly you did to do the upgrade, so am I right to assume the purpose of this thread was to rant about UUIDs instead of asking for help with some problem with Ubuntu?

---

### Post by skypuppy on 2011-05-14
both.  The questions are both there.

---

### Post by Lateralis on 2011-05-14
Hi Skypuppy.  

I would firstly like to direct you to the first link in my signature.  I can understand that you are hugely frustrated right now, but ranting and raving isn't the most efficient way to solve your problem(s).  In the first instance people will simple assume the thread is a rant thread.  In the second, people will be less inclined to help as it sometimes feels like a direct attack.  

Secondly, if you actually want help, you will need to be far more descriptive.  What is your hardware configuration?  Are you using RAID and how?  Did the upgrade apparently go OK?  Have you tried editing the grub line at boot up to see if different options allow you to boot?  Have you tried using any method of recovery using a LiveCD?  Have you [searched]("http://ubuntuforums.org/showthread.php?t=591746") [the]("http://ubuntuforums.org/showthread.php?t=1749861&highlight=initramfs") [forums]("http://ubuntuforums.org/showthread.php?t=1756529&highlight=initramfs") for similar topics?  

All these things will help us help you.

On another level, you may also want to run the [boot info script]("http://bootinfoscript.sourceforge.net/") in a LiveCD session and post the results here.  This will tell us exactly what your system is trying to do at boot.  You may also want to check out the extensive information in the Upgrade Problems link in my signature.  The first post covers many topics, some of which may be of interest.

---

