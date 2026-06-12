---
title: "grub 'mislabels' windows partitions"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by bistro on 2010-05-10
Hi

I have upgraded to 10.04. Everything works but unfortunately
 in grub the vista loader is shown as sda1 and the windows recovery environment as sda2 - in fact they are the other way around. As this is a computer shared by the family and I'd like to fix that.

Thanks in advance

Dave S

---

### Post by lisati on 2010-05-11
I noticed a similar effect when I installed 10.04, but haven't got round to dealing with it yet.

---

### Post by bistro on 2010-05-11
Hi

thanks for your reply, hadn't noticed but the issue had been raised in an earlier thread [here]("http://georgia.ubuntuforums.org/showthread.php?t=1469755&page=1") but not really solved there either.

Dave

---

### Post by oldfred on 2010-05-11
Put just the one windows entry in 40_custom and turn off osprober so it does not find you windows. You can turn it back on later if you want to:

Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
OR:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu. Or you can copy it to 09_custom and make it executable and it will be at the top of your menu.

---

