---
title: "grub rescue&gt;"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by new__buntu on 2010-07-18
I'm moving from a dedicated partition for ubuntu to a wubi install on one of my machines, and I used the live disc to remove the old installation and resize windows so that it could take the whole disc - and now when I try to boot up I get taken to grub rescue>. How do I get my computer back to a standard windows boot?

---

### Post by Zorgoth on 2010-07-18
The problem is probably that you have a grub which relies on /boot/grub existing, and by wiping out the partition containing it, you destroyed that.  At this point, if you have the Windows XP CD you have lots of options, if not try finding a way to boot into Windows (perhaps using Auto Super Grub Disk), and if you can get in, use mbrfix or mbrfix64 (mbrfix for 32-bit, mbrfix64 for 64-bit), and if you can't, you can try booting from an Ubuntu live cd and downloading ms-sys from the repository.

If none of that works or if you aren't comfortable with it a dirty solution is to install a new Ubuntu, either on the hard drive or on a device like a USB thumb drive, setting it up so it can boot the Windows (that shouldn't be a problem) and then booting into Windows and doing Windowsy things like mbrfix or whatever.

---

### Post by new__buntu on 2010-07-18
> **Zorgoth said:**
> The problem is probably that you have a grub which relies on /boot/grub existing, and by wiping out the partition containing it, you destroyed that.  At this point, if you have the Windows XP CD you have lots of options, if not try finding a way to boot into Windows (perhaps using Auto Super Grub Disk), and if you can get in, use mbrfix or mbrfix64 (mbrfix for 32-bit, mbrfix64 for 64-bit), and if you can't, you can try booting from an Ubuntu live cd and downloading ms-sys from the repository.

If none of that works or if you aren't comfortable with it a dirty solution is to install a new Ubuntu, either on the hard drive or on a device like a USB thumb drive, setting it up so it can boot the Windows (that shouldn't be a problem) and then booting into Windows and doing Windowsy things like mbrfix or whatever.

Thanks, I ended up using mbrfix. Now to add wubi :)

---

