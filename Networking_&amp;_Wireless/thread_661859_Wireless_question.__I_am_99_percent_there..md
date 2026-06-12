---
title: "Wireless question.  I am 99 percent there."
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by jmclein on 2008-01-08
Hello all.  Let me start by saying how impressed I am at the wonderfully helpful community I have found here.  I have been a long time IT person.  I have worked on MAC's and Windows boxes my entire life but never Linux.  The support I have found within these forums is unbelievable.

My question is as follows. Using the steps located at [http://ubuntuforums.org/showthread.php?p=4016195](http://ubuntuforums.org/showthread.php?p=4016195) I managed to solve both those problems on my gate ML6720.  My only small remaining problem is a portion of the wireless.  It seems to me that the system isn't loading the drivers automatically.  If I run the command "sudo modprobe ndiswrapper" the wireless will load and everything will work fine.  However when I run the "sudo ndiswrapper -m" command I get a output of "module configuration already contains alias directive"

I am thinking that isn't right and that is what is stopping the system from loading the wireless drivers on bootup.  Does anyone have any advice?

Thanks!

---

### Post by luisromangz on 2008-01-08
You can force the loading of the drivers at boot time adding that command to the file /etc/rc.local.

Quite non-elegant, I know, but works well.

---

