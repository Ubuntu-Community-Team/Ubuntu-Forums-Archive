---
title: "grub or grub2 which is better?"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by eddski on 2010-11-18
which ver of grub is better? if grub2 is better how do i remove the old and install grub2?

---

### Post by libssd on 2010-11-18
> **eddski said:**
> which ver of grub is better? if grub2 is better how do i remove the old and install grub2?

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by oldfred on 2010-11-19
I consider grub2 better, but if you still are running 9.04 the version you would get is early and each version has major updates.

If grub legacy is working I would stay with it unless you have having problems. I used grub legacy up to 9.04 and the only issues I had with grub2 were with understanding the new way it does things.

General info:
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by Rubi1200 on 2010-11-19
I agree with oldfred that GRUB2 is the way to go unless things are fine as is, in which case better to leave well alone.

Also, bear in mind that most users have GRUB2 and, as a result, most support requests and solutions deal almost exclusively with GRUB2.

---

### Post by santosh83 on 2010-11-19
> **eddski said:**
> which ver of grub is better? if grub2 is better how do i remove the old and install grub2?

Grub2 might certainly be superior to legacy Grub, and the way to go, but what I do know is changing the boot commands and options in menu.lst was much simpler than the current situation involving fiddling with many files in /etc/grub.d and /etc/default/grub.

---

### Post by lisati on 2010-11-19
My laptop has grub2, installed when I did a fesh install of 10.04, and I haven't had the need to tinker with it. 

My server has legacy grub, mainly because I originally put 9.04 server edition on it, and didn't see a pressing need to update grub when updating the OS.

---

### Post by indytim on 2010-11-19
It's entirely a personal preference.   GRUB2 is the blazing current technology.  As you scan the boards, you will find frequent posting to the difficulties in "customizing" in the GRUB2 environment.  As an earlier poster mentioned, maintaining  the menu.lst is much easier if you are remotely capable of light file editing.

For me, I have maintained my dedicated GRUB legacy partition which I boot to.  When adding a new ops these days, I just opt out of the install GRUB (advanced features).  When the install is completed, I merely add the new stanza to my menu.lst, refresh GRUB and I'm ready to proceed.

Another perspective.... :p

IndyTim / DataMan

---

