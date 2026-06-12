---
title: "uninstalling unwanted distros"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by robjcor on 2009-08-18
I'm a new linux user, and I started by installing several distros on my 40Gb hard drive.  I've now settled on Ubuntu (Intrepid) and I want to uninstall the others to make more room.  This is either so easy that it isn't worth mentioning anywhere (and I have looked everywhere I can think of) or only possible with a Windows CD (I don't have Windows on this machine), and even then only with considerable difficulty.
As far as I can make out, simply deleting the partitions for Suse, Debian and so on will create problems with GRUB.  Is this so, and is there a simple solution?
I know that I can't be the only person with this problem, so if there's anyone out there who can point me in the right direction I'd be very grateful.  
Thanks, Bob

---

### Post by realzippy on 2009-08-18
gparted should do the job...

---

### Post by robjcor on 2009-08-19
> **realzippy said:**
> gparted should do the job...

OOPS!  I should have asked a few more questions here.  I deleted unwanted partitions with gparted and now get grub error 17 on booting.  I thought that seemed too easy.  Any further suggestions welcome.  Bob

---

### Post by mcduck on 2009-08-19
Just delete the useless partitions, and after that re-install Grub.

Here's one guide for re-installing Grub:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

If you also expand your current Ubuntu partition to use the available space this will change the partitions UUID, so you'll have to edit your /etc/fstab accordingly to use the new UUID. You can check the new UUID with the "blkid"-command.

And no, you don't need Windows CD to fix Linux installs. Some of us might find suggesting such things insulting.. (just kidding :D)

---

### Post by realzippy on 2009-08-19
...SuperGrubDisc restores GRUB easily:

[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

---

### Post by robjcor on 2009-08-21
First of all thanks very much to realzippy and mcduck.  Everything is now sorted and working fine.  I really appreciated your help.

Just in case anyone else reads this with the same problem, there were a couple of twists in the story which may be useful.  First of all, I tried the basic method given on this link from mcduck.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

It didn't work, so I downloaded an image from

[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

as suggested by realzippy, burned it to cd and booted.  No problems, straight into the lost ubuntu partition - it was good to see it was still there.  BUT the disk didn't change anything, and when I removed it, error 17 reappeared.
I booted from the cd again, followed the more advanced technique beginning sudo mkdir /mnt/root from [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351), and this time everything was fine.  Hooray!

A couple of points arise.  First of all, did I download the correct supergrub disk?  There were so many downloads to choose from that I may not have done.  I downloaded the grub rescue disk.

Secondly, I have another computer (running windows at the moment, sorry!) so there wasn't a problem accessing information on this forum even when I couldn't boot into ubuntu.  But what could I have done to avoid all these problems in the first place?  If anyone out there can tell me, I'm sure it would be helpful to others in the same situation.  I couldn't find anything relevant when I searched.  The only thing which cropped up again and again was if you were dual-booting linux and windows, not if you had multiple linux distros and wanted to get rid of some of them.

Anyway, thanks once again for your help.  I love the linux philosophy, and this forum convinces me that linux is the way to go.

---

