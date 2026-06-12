---
title: "Can you install 9.10 on Flash Drive?"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by WubiNoob on 2010-02-18
Can you install a copy of Ubuntu 9.10 on a 2GB Flash Drive, essentially running the full distro, not just the live CD version, on a flash drive? Will it save files? Will hardware work properly? Thanks, help is appreciated.

---

### Post by wilee-nilee on 2010-02-18
No the basic Ubuntu 9.10 unpacks to about 2.4 gigs.
I have a 16 gig thumb with a full install of Lucid on just a primary partition no swap. This could be done on a 8 gig thumb and be quite usable.

There are other smaller distros that are worth considering, I am not sure beyond puppy linux.

---

### Post by WubiNoob on 2010-02-18
Storage capacity is not a huge problem for me, but if you had enough space on the flash drive itself, could it use the full OS? Thanks

---

### Post by dmaxel on 2010-02-18
Flash Drives aren't ideal, as the full OS does a lot of read/write operations, which could fail the flash drive. Try using an external (USB) hard drive instead. This is what I am currently using too, but I am having some problems, as I want it to be able to boot on all systems I plug it into.

---

### Post by wilee-nilee on 2010-02-18
> **WubiNoob said:**
> Storage capacity is not a huge problem for me, but if you had enough space on the flash drive itself, could it use the full OS? Thanks

In the end if you do a full install on a external device like a thumb make sure that grub is pointed at it when you get to the last install confirmation screen under advanced.

---

### Post by sgosnell on 2010-02-18
Yes, you can install on a flash drive.  I have Lucid installed on an SDHC card, and still have Jaunty on an 8GB USB stick.  Works fine.  It may not be quite as snappy as an internal drive, but it's quite tolerable.  The writes to disk aren't really a problem, since it will take years to wear the drive out, running 24/7.  Mark the drive as noatime instead of relatime in fstab to reduce small writes and improve performance marginally.  In any case, flash drives are cheap.  As wilee-nilee said, make sure you install the bootloader on the flash drive, not on the internal drive.  Otherwise you won't be able to boot without having the flash drive attached.

---

