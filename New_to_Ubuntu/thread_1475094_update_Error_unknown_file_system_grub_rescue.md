---
title: "update Error unknown file system grub rescue"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2010-05-06
So, My friend just upgraded from karmic to lucid and she now gets "Error, Unknown file system grub rescue" and cant access ubuntu or her vista partition. Wat do?

---

### Post by HarrisonNapper on 2010-05-06
Well, first things first, boot from a live USB. Then from a terminal run fsck on the Linux partition. I'm not sure if that will help since it sounds like it may be a grub error, but worth a try.

---

### Post by TheNerdAL on 2010-05-06
This might help: [http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/](http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/)

---

### Post by LunaticHiatus on 2010-05-06
supergrubdisk seems like the easiest way, anything I should know about it?

---

### Post by LunaticHiatus on 2010-05-06
well that was a failure, gonna try to boot up from livecd now

---

