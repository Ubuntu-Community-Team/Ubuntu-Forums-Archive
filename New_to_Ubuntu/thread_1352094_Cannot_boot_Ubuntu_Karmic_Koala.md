---
title: "Cannot boot Ubuntu Karmic Koala"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by cremebrulee1979 on 2009-12-11
Hi,

It's my first time posting in this forum, and somewhat of a beginner. For the most part, Ubuntu runs very well and I hardly have any issues with it. There are times in which I use it for days and not load Vista at all, and sometimes it's the main OS for the everyday tasks I do and for some games.

However, one day after choosing over Vista the OS to boot, Ubuntu won't start as usual---instead, what greeted me onscreen was this:

------------------

GNU GRUB version 1.97~beta4

[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB list possible device/file completions.]

sh: grub>

------------------

Can someone point to me a page where I can find help to troubleshoot this problem? I can't find the words to use in search to come up with the page that can help me. If you can post the solution/s here, I would be grateful!

THANKS!

---

### Post by RyanVanDiemen on 2009-12-11
Hi, apparently you`re in the grub shell. Not sure how did that happen, but wiki page below, should help you. You can easily restore the grub by copying it from the CD and update it - see the section Recover Grub 2 via Live CD. Don`t be confused by ver. 1.97 - it is actually grub 2. I`m still not familiar with grub 2 (it`s quite different than the old one), but this worked for me when OpenSUSE installation damaged my MBR grub install (although I told him to install SUSE grub to its own partition...).

[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

---

### Post by Yvan300 on 2009-12-11
Try reinstalling grub by following the instructions here [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351).

---

### Post by philinux on 2009-12-11
> **Yvan300 said:**
> Try reinstalling grub by following the instructions here [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351).

The link you provided is for grub-legacy and will not work. The OP is running grub2. See link in my sig for grub2 info.

To recover grub2 follow this guide.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by cremebrulee1979 on 2009-12-11
thank you, will try the solutions all of you posted :D *crosses fingers*

---

### Post by Yvan300 on 2009-12-11
Sorry my bad :)

---

### Post by cremebrulee1979 on 2009-12-16
hello,

the solutions didn't work :( i had to take out ubuntu from my laptop...good thing i have backup of my files.

thank you anyway...:)

---

