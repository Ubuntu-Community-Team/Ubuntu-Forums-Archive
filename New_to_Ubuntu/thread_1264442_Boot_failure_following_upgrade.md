---
title: "Boot failure following upgrade"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by bwallum on 2009-09-12
Hi

I have just upgraded my Jaunty AMD64 system after some 3 months of neglect. The hard drive had filled up with Trash and backups. I removed them and got some 35GB back. I then updated and ....I got the following on a black screen when rebooting as advised:-> [*some numbers*]USB 1-7 new high speed USB device using ehci_hcd and address 2Fine, but it didn't move on. I have had a look at the grub menu.lst file which appears ok. 

Could it be the mbr? How do I check what is in the mbr? Any other ideas?

Thanks, Bob

---

### Post by philinux on 2009-09-12
I would do this. Reboot.

At grub press esc and choose the recovery mode. See where that gets to. If you get to the recovery menu choose resume normal boot.

Oddly, sometimes a couple of reboots sorts things out.

---

### Post by bwallum on 2009-09-12
Thanks for the steer. Running in recovery mode I got:> WARNING: boot device may be renamed. Try root=/dev/sda1....and a lot of other advice followed by > ALERT /dev/hda1 does not exist. Dropping to a shell!then Busybox started.

I booted up with my external drive and using ```
gksudo gedit /media/disk-1/boot/grub/menu.lst
``` changed the listed boot options to root=/dev/sda1. (For anybody following my problem drive was called disk-1 but yours may be called something else)

It worked! Now having upgraded the kernel I need to reinstall my nvidia driver (64 bit and version 185. ...not yet in repositories)

Thanks again philinux!

---

