---
title: "Grub Error 15 after upgrading to grub2; can I reinstall grub from Live CD?"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by diablo75 on 2010-11-06
A friend of mine just upgraded Ubuntu 9.04 strait to 10.04.1 and grub wasn't upgraded during the process, so I've been trying to help him do it manually using the Ubuntu Community Documentations for grub2.

We decided add a chainloader to grub 2 from grub 1 as instructed and during this we hit the Error 11 snag where, if you selected the Chainloader, it wouldn't work.  Following the guide, we tried to edit the word "root" to "uuid" per the instructions but this just resulted in the computer instantly rebooting.

I decided (poorly) to run the upgrade package anyway, dreaming that the problem would work itself out.  Well I was wrong.

So I'm heading over there now and was looking for a quick fix.  I'll be taking a Live CD with me and would love to just be able to punch one or two no-brainer commands in so that GRUB will reinstall completely and correctly.  Is this possible?

---

### Post by Rubi1200 on 2010-11-07
You need to choose: either keep legacy-GRUB (which I do not recommend) or use GRUB2 (recommended).

For the error mentioned in the title:
[https://help.ubuntu.com/community/Grub2#File%20Not%20Found%20%28Error%2015%29](https://help.ubuntu.com/community/Grub2#File%20Not%20Found%20%28Error%2015%29)

I recommend a full purge and reinstall of GRUB using the chroot method outlined here:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

