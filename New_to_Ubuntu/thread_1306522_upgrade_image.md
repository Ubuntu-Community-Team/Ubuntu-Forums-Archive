---
title: "upgrade image"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by supermooshman on 2009-10-30
hey all,

I kind of feel stupid to ask... but guess better to feel stupid than to screw it up (which I actually already did ;))

to upgrade from jaunty to karmic through an iso downloaded from torrent - which one do I use? the alternative or regular image?

I just tried the regular image and mounted it using:  
sudo mount -o loop ~/Desktop/ubuntu-9.10-alternate-i386.iso /media/cdrom0no dialog box came up nor did Alt+F2:  gksu "sh /cdrom/cdromupgrade" help in any way. Anyone knows?

ps: don't know if it would make any difference but I use UNR

---

### Post by qamelian on 2009-10-30
You need to use the alternate CD to upgrade from CD. The Desktop CD just contains a compressed bootable filesystem, not the actuall installation packages, like the Alternate CD.

---

### Post by QIII on 2009-10-30
Do you want to "upgrade" or "reinstall"?

They are two different beasts, and you may not be happy with the results of one or the other.

---

### Post by supermooshman on 2009-10-30
> **QIII said:**
> Do you want to "upgrade" or "reinstall"?
.

I want to upgrade (get karmic instead of jaunty - while keeping my files)
so still the alternate image?

---

### Post by supermooshman on 2009-10-30
> **qamelian said:**
> You need to use the alternate CD to upgrade from CD. The Desktop CD just contains a compressed bootable filesystem, not the actuall installation packages, like the Alternate CD.

oh, and it wouldn't matter if I use the alternate desktop to upgrade my netbook remix?

---

### Post by ranch hand on 2009-10-30
Back up your files and do a clean install.  Put your files back in.

Look at the forum list of people having trouble with upgrades.  Not a good idea.

---

### Post by QIII on 2009-10-30
Just by way of terminology --

**apt-get update **and **apt-get upgrade **-- update the package lists, then get the latest stuff for your current version

**Upgrade** (the version.  Not to be confused with "sudo apt-get upgrade", which is part of the above)  -- get all the new stuff for the newest version and replace the old system files with the new while preserving your personal files.  For this, you do not need an image.  It can be done from the command line with "do-release-upgrade" or by opening the Update Manager.  When a new version comes out, a button is available for you to choose the new.  Be prepared for a long wait, since the servers will be very busy for the next week or so.  In the case of Karmic, that will leave you with the legacy GRUB and an ext3 file system.  If you really want to do this, upgrade to GRUB2 and ext4 first.  Be aware that upgrading to ext4 will not change the format of your current files.  They will still be ext3, but the will still work.  Use Synaptic's tools to make a list of your installed applications (installed through Synaptic only. You are on your own for third party installations.) If you have a separate /home partition, back it up somewhere safe to keep all of your data.  If you don't, back it up anyway!  If the update fails, you still have your /home partition and a list of your installed applications, which can be used by Synaptic to reinstall them all if need be.  Be aware that if you drag your /home partition back where it came from (if it is not separate), you may end up with some permission problems and you'll have to do some work to get some profile files (like Firefox and your email app if they are upgraded while doing this) tied back together.  If the upgrade succeeds, you won't need to do any of that.  The big thing about upgrades is that a lot of people experience a great number of frustrating problems after doing it.  Things have gotten better, as I understand it, but old habits die hard for this old Soldier.

**Fresh install** -- If you have a separate /home partition, save apps through Synaptic as above.  Back up your /home partition just in case.  I think I might still upgrade at least that directory to ext4 before moving on, though.  The rest is easy peasy.  Just run the installation disk -- BUT DON'T reformat your /home partition.  Unless you have an utter catastrophic failure, your /home partition will be just fine.  You won't have to replace it or update most of your profile type stuff.  But since Karmic installs with Firefox instead of Shiretoko, the profile folder is in a different place and you'll have to drag all the contents of your original Shiretoko (or FF 3.0) folder into it -- or make sure that the first time you open Firefox you link to it.  I think that can be done.  Take care with things like your email app as well, if it has a profile folder.

Unfortunately, if you do not have a separate /home partition you will have to save the one you have, create a partition mounted as "/home" when running the installation and then drag the saved /home contents into that.  Again, however, profiles and such may be whacked.  Your /home partition should take up the lion's share of your disk.  Swap should take 1.25x - 2x of the size of your RAM.  "/" (this may change depending on how many other partitions you want to create) maybe 15G. Don't make it too small, because the OS has to fit. If you plan to install some fantastic number of applications, maybe 30G.  That depends, of course, on the size of your disk.

In any case, when you reinstall, make sure to create a separate /home partition to make this easier in the future.

There are ways to create a separate /home partition in your current version if you do not have one and then transfer the contents of your current /home to it.  I have never gotten any of those methods to work satisfactorily.

---

### Post by supermooshman on 2009-11-01
Finally 9.10, what a nightmare!

apparently if you use the update manager you need more available space than on an eee (4gb+16gb) is available.

Plegh
anywho, solved the problem by following ranch hands advice, backup and fresh install (still it doesn't really seem right to do this?)

---

### Post by ranch hand on 2009-11-01
There are a lot of changes in 9.10 and residual stuff from 9.04 is not always compatible.

If you have a separate / and /home partitions it makes this process a lot easier.  I always do a clean install because you do not have a bunch of files that, while they may hurt nothing, do nothing except take up space.

If you use a torrent to download the LiveCD, the whole precess is a lot faster than upgrading too.

Even if you upgrade you are recommended to back up all your data because there is always the risk of loosing all, or part, of it.

---

