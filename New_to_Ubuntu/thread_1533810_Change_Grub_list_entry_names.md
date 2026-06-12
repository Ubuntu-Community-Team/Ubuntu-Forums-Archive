---
title: "Change Grub list entry names"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by MockY on 2010-07-18
Grub2 is a little confusing, but until now I don't remember having any issues with changing the boot order nor the names of the listings.

What I want to do is remove some of the entries, change the name of the ones I want to keep, and change the boot order.
/etc/default/grub which seems to be the only file allowed to change, does not even have the listings, so how would I be able to change the name of them?

Could someone please steer me in the right direction?

---

### Post by cariboo on 2010-07-18
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=1287602") thread.

---

### Post by oldfred on 2010-07-19
If you really want to do a totally custom menu, you can or as I did a partial custom menu.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by MockY on 2010-07-20
Even though I have uncommented the following line
```
GRUB_DISABLE_LINUX_RECOVERY=true
```
the recovery menu entry is still generated when I do a sudo update-grub

Why is that, and is there another way to remove the recovery entry?

EDIT: By hitting 'F', the recovery entry disappeared. However, I thought that it would not even be generated once that option was enabled.

---

### Post by redo.blackpool on 2011-03-25
where's the answer?

---

