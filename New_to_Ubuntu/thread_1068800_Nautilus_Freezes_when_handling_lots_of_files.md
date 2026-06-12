---
title: "Nautilus Freezes when handling lots of files"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by dasc on 2009-02-13
Hi, I thought I posted it awhile back but it seems that the post is gone or i didn't submit it properly.........

I've been using ubuntu for about 7 to 8 months now and really like how stable it is (except for the minor glitches here and there) but unfortunately I've hit a problem when dealing with large amounts of files.

I have a directory that has over 20,000 files and when i try to open it with nautilus it freezes!!!!!  I've tried letting it load for an hour and it's still not responded.  Has anyone tried nautilus with 100 to 200 thousand files?

---

### Post by jou770d on 2009-02-13
It's still there, just in an another category:
[http://ubuntuforums.org/showthread.php?t=1059772](http://ubuntuforums.org/showthread.php?t=1059772)

I've never dealed with that many files but nautilus crashes sometimes for me if I installed certain scripts, such as nautilus-play-amarok or nautilus-tag-music from [http://mundogeek.net/nautilus-scripts/](http://mundogeek.net/nautilus-scripts/)
I don't know if that would help...

---

### Post by kaibob on 2009-02-13
> **dasc said:**
> Hi, I thought I posted it awhile back but it seems that the post is gone or i didn't submit it properly.........

Your earlier thread is at:

[http://ubuntuforums.org/showthread.php?t=1059772](http://ubuntuforums.org/showthread.php?t=1059772)

You can find all your posts by clicking on "Search" near the top of this web page and then clicking on "Find All Your Posts."

I do not have any directories with 20,000 files, but I do find Nautilus slow when opening directories with a large number of files. I don't have any solution to this--sorry that I can't be of more help.

---

### Post by aev on 2009-02-13
Yes, Nautilus freezes or is very slow in Ubuntu 8.10 . Very annying. I wrote in another thead too. Just want to make sure people see it and homepfully wew ill have a solution soon.

---

### Post by dasc on 2009-02-16
Thanks guys for helping me find back my older post, but it seems that no one has ever replied my older post! >_X;

For now I think i'll manage with the console, but has anyone tried alternative file managers and is it hard to get used to it?

---

### Post by m4cph1sto on 2009-02-24
I have the same problem, Nautilus is painfully slow when displaying more than a few dozen files, and freezes completely when viewing very large folders.  It must be a very serious bug, because it makes it almost unusable for some people.

I installed Dolphin (the KDE file manager), and it seems to work flawlessly, opening large folders instantly.  Of course it has its own list of default applications for opening files, so it's a slight hassle - but much better than Nautilus!

*Update*
I've always been using Nautilus in "list view" mode.  I just switched it to "compact view", and it displays folder contents MUCH more quickly, and never freezes.  This got me searching, and:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/159042](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/159042)

It seems if you disable "assistive technologies" (and log out then in), the bug with list view goes away.  I'll try it in a minute, but hopefully that'll fix your problem.

---

### Post by m4cph1sto on 2009-02-24
Yep, disabling assistive technologies fixes the problem.  Nautilus is now snappy as can be.  I think you can mark the thread [solved] now.

---

### Post by mkvnmtr on 2009-02-24
Thanks I have just been having problems viewing a usb stick and it freezing.

---

