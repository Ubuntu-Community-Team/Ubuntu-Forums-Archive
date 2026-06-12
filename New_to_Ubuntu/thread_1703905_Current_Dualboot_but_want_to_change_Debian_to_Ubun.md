---
title: "Current Dualboot but want to change Debian to Ubuntu on the Linux side"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by soulman555 on 2011-03-09
I currently use Windows XP as my main OS and would like to change to Ubuntu with occasional Windows programs under VirtualBox (need Dragon Naturally Speaking, Lightroom, and Photoshop).  I had installed Debian several years ago for a dual boot system, and GRUB is my bootloader (although I just followed instructions and have no idea how this worked or how I set this up initially).  How do I remove Debian and install Ubuntu in its place without messing up my system or making it so that Windows can't load.  I would prefer to keep my current Windows XP as an option to load in case the VirtualBox Windows environment is not as successful as I hope.  Thanks for any help!

---

### Post by Matt__ on 2011-03-09
first off, boot using ubuntu as a live disk and check everything works ok.

then it should be a simple case of choosing 'specify partitions manually' during the install process and choosing your current debian partition to write ubuntu to. It will wipe that partition during the ubuntu install and update grub at the end of the process leaving you with a dual boot with xp.

---

### Post by soulman555 on 2011-03-12
Thanks!  Ended up installing Linux Mint for now, as I couldn't get my sound to work with Ubuntu (did go through the extensive troubleshooting guide without success).  Very well might try back but will play with Mint for now.

---

