---
title: "grubproblem"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by chilimac02 on 2009-12-15
I had a crash... boot up and I get 

GRUB loading.
error: unkown filesystem
grub rescue>

Ummmm.... help?

I tried putting 9.10 on a usb stick to reinstall, but it doesn't work. I keep getting the same screen. I even made usb the first boot option, and nothing changed...

---

### Post by Bucky Ball on 2009-12-15
Are you dual-booting with Windows? If so, can you boot into Windows? If you can, boot in, shut down (not restart) and try again.

---

### Post by chilimac02 on 2009-12-15
yep dual boot xp, but no chance of booting into xp because I can't get past the grub recover screen

---

### Post by oldfred on 2009-12-16
If you know your partitions you can use the grub command line. I never had to but this is a reference, scroll down a page or two:

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

---

### Post by chilimac02 on 2009-12-16
OK, now I'm a little worried. None of the grub commands are being recognized.

example:
grub rescue> dump
Unkown command 'dump'
grub rescue> normal
Unkown command 'normal'

any ideas? I think I screwed up grub too in there somewhere...

---

### Post by chilimac02 on 2009-12-16
ok, got passed it. I had to change the BIOS setting from primary HDD is my hard drive to primary HDD is my USB key. I wouldn't have thought that, since the USB key was first on the boot order... Oh well.

---

