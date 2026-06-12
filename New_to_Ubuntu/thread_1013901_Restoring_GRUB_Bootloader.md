---
title: "Restoring GRUB Bootloader"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by x0prah_Winfr3yx on 2008-12-17
Hello all. Last night I tried re-installing my OS X onto an empty 40gb partition. Well, let's just say the Darwin Bootloader get's me past the gray Apple screen, only to stop on a blank blue screen. Not cool.

Back to my problem, I can't seem to get my system to get back in the habit of booting through GRUB. The OS X DVD i have let's me flag different partitions to boot from, but i've tried all four partitions and without any success, they still go through Darwin.

I'd post in Insanely Mac Forums about this problem, but it's got to be the worst forums for getting a response, an opposite of this forum.

Thanks in advance.

---

### Post by Hospadar on 2008-12-17
Probably osx just wiped your mbr (the master boot record) so now even when you try to boot your ubuntu part. there's no bootloader (because grub was in the mbr, not specifically on that partition).

The good news is, it's probably easy to fix!  It'll involve you booting off a livecd and getting into the grub console.

These pages explain it pretty well:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

After you get booting into ubuntu, if you don't see osx on your boot list, try running a "sudo update-grub"

---

### Post by x0prah_Winfr3yx on 2008-12-17
surprised i didn't think of that. thanks!

---

