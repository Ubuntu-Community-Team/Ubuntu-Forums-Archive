---
title: "Trying to get Ubuntu working w/ Windows 7"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by mariakk on 2011-08-05
Hey everyone :)

I downloaded Ubuntu onto my flash drive today (my CD drive doesn't work) and booted from the USB after I'd configured it. I started installing it but then I got to the screen where you're supposed to decide where you're going to install Ubuntu.

The first thing I noticed is that I didn't get an option to choose "Install Windows 7 and Ubuntu side-by-side" like I read about online. I know it's best not to choose that, but it wasn't even an option.

So I clicked the setting to configure it yourself, because I don't want to uninstall/replace Windows 7. Then the "Allocate drive space" window showed up.

The devices available are:

/dev/sda
/dev/sda1 (ntfs)
/dev/sda2 (ntfs)
/dev/sda3 (ntfs)

sda1-3 all have a "size" but the one for /dev/sda is blank. There isn't an option to create a new one, and whenever I click one and try to change it, it automatically checks the "Format" blank even though I don't want to format.

How do I install them side by side?

---

### Post by wildmanne39 on 2011-08-05
Hi, that is probably because you already have four primary partitions so you will have to delete one first.
Here is a guide on the subject.
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

---

