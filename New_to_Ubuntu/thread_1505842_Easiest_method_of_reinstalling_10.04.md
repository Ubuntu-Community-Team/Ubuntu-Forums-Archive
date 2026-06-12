---
title: "Easiest method of reinstalling 10.04"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by Zappanale on 2010-06-09
I'd like to do a fresh install of 10.04 on my laptop, which is currently dual booting alongside windows 7. Can anyone please tell me the easiest/most convenient way to go about this? Thanks.

---

### Post by mbzn on 2010-06-09
Backup first...
Do you have a separate /home partition?

---

### Post by ManfredKlinglmair on 2010-06-09
Same question here!
I'm running 10.4 alongside Win XP, but several things that worked in 10.4 two days ago (after installation) do not work any more. So I'd just like to go with the time-honoured technique of uninstall-install again.
How do I do this nice and clean? (While keeping WinXP untouched) :-)

Thanks!

---

### Post by bodhi.zazen on 2010-06-09
Insert ubuntu CD 

reboot

Install

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Install into the old partitions.

You do not need to remove or change anything to perform a fresh install over the top of the old.

The installation process will format the partitions, so back up any data you do not wish to loose.

Is there a specific problem you have ?

---

### Post by mbzn on 2010-06-09
Ok, when booting the live cd, and clicking install as you did before.
when it comes to partitioning you can do it manually(the last option)

now lets say: sda1 = windows
sda2 is /
sda3 is /home
and sda4 is swap   (please make sure you don't delete the wrong one)
(if there is no separate /home you will lose your home directory, a fresh one will be overwritten)

ok now, select the sda2 partition and say change, use ext4(or whatever)
check the format option and mount as /
For /home(if separate) do the same, mount as /home, use the same file system as before and DO NOT check the format option

The swap will sort itself and leave the windows partition untouched.

This should get you going, and happy Ubuntuing

---

### Post by ManfredKlinglmair on 2010-06-09
Since I am still trying out Ubuntu, but some issues have come up (graphics were no problem - now I cannot change visual effects any more due to some update, I suspect), can I not just remove Ubuntu? And then reinstall it alongside WinXP as if it had never been there?
Asked differently, how do I remove Ubuntu? (So that it can resurrect in old glory, of course!)

M.

---

### Post by bodhi.zazen on 2010-06-09
> **ManfredKlinglmair said:**
> Since I am still trying out Ubuntu, but some issues have come up (graphics were no problem - now I cannot change visual effects any more due to some update, I suspect), can I not just remove Ubuntu? And then reinstall it alongside WinXP as if it had never been there?
Asked differently, how do I remove Ubuntu? (So that it can resurrect in old glory, of course!)

M.

Depends on how you installed it, standard or wubi ?

---

### Post by ManfredKlinglmair on 2010-06-09
Standard, I suppose. And please forgive my ignorance in all things Ubuntu, but what is wubi?

M.

---

### Post by bodhi.zazen on 2010-06-09
> **ManfredKlinglmair said:**
> Standard, I suppose. And please forgive my ignorance in all things Ubuntu, but what is wubi?

M.

Wubi :

[http://wubi-installer.org/](http://wubi-installer.org/)

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

Instructions for removal of wubi are on those pages.

Standard :

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

Although there are other sets of instructions for removal of you google, I believe even Microsoft has a page on removing Linux.

---

### Post by ManfredKlinglmair on 2010-06-09
Ok, learned a new thing there. Thanks.
Just wondering why searching the forums for 'remove ubuntu' did not get me to that page.... hm hm.

Cheers M.

---

