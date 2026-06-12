---
title: "Moving hard drive over to new computer/fsck question"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by slothario on 2010-12-30
I had a Linux installation in an old computer and I want to move it over to a new one. So, I popped the hard drive in the new computer, and when I started it up it gave me "Mount of filesystem failed. <some error code I forgot>. A maintenance shell will now be started." Other forum posts say to run fsck, which I'm doing right now, but I see no visible progress and the hard drive isn't clicking away. It seems it would use the hard drive a lot if it's trying to fix the file system. What gives? Also, I should probably note that I hard reset the old computer a few times before I turned it back on, so that could have been part of the problem. Oops...

---

### Post by slothario on 2010-12-30
Oops, sorry for my impatience. Fsck worked like a charm - I just had to give it about 20 minutes.

---

### Post by tgalati4 on 2010-12-30
If your boot loader is using a UUID instead of /dev/sda1 for the drive/partition, then it may have changed.

Boot with a LiveCD, open a terminal:

blkid


Mount the drive and make changes to /boot/grub/grub.conf or menu.lst and you should be able to reboot from the drive.  It's a common issue when swapping drives.

---

