---
title: "Grub 2 won't boot windows 7 after upgrade"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by prover on 2010-05-02
Hi, when I upgraded my xubuntu from 9.10 to 10.04 I chose to keep my old grub (legacy). This went almost well... Both Windows 7 and Xubuntu booted, but xubuntu used a lot more time booting now than before.

I figured that maybe upgrading grub to grub2 would help. Now the new grub-menu appears with both xububtu and windows 7, but nothing happens when I try to boot windows 7.

Do anyone know what might be wrong, or what to do?

---

### Post by nitstorm on 2010-05-02
ubuntuforums.orgubuntuforums.org/newreply.php
Try [this]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

---

### Post by Paul T. on 2010-05-02
You might want to read this post, seems to be a known issue:

[http://ubuntuforums.org/showthread.php?t=1469314&highlight=boot](http://ubuntuforums.org/showthread.php?t=1469314&highlight=boot)

---

### Post by prover on 2010-05-02
Thanks for the quick answers!

I tried nitstorm's link, which, after trying out "testdisk", advised me to use the windows installation disk and fix the mbr/boot from there. Now the pc boots directly to the windows recovery partition. :(

Then I have tried to reinstall grub from a live-usb. Where do the changes I do from live-mode apply?

"find /boot/grub/stage1" gives me: "Error 15: File not found"

Any ideas? :)

---

### Post by prover on 2010-05-02
:) you guys don't have to bother with this problem anymore. I have struggled with this for several days now and learned a lot. But being a new linux-user, I want a fresh start. So I'm reinstalling linux and hoping for better "luck."

---

