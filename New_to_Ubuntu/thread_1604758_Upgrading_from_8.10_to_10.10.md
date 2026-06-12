---
title: "Upgrading from 8.10 to 10.10?"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by egkeat on 2010-10-24
I'm absolutely confused about using Ubuntu after many many years of Windows.  So how to upgrade after installing from my old 8.10 disk? (I tried 10.10 several times but kept getting a permission denied error). Do I upgrade to 9.04, and how to I go about doing that?  Or can I install 10.10?

---

### Post by jgeralnik on 2010-10-24
Try running sudo update-manager -d and seeing if it let's you upgrade.

---

### Post by oldfred on 2010-10-24
Make sure you have backed up all your data, particularly everything in /home. 

If you want to upgrade you have to do each one in order. 8.10->9.04->9.10->10.04. (8.04LTS will let you go directly to 10.04LTS) Each upgrade may of course have some issues, so it may be better just to install 10.10 and be done with it. Try the liveCD to make sure your system works. Often f6 on livecD and settings to get video to work are often required.

If you have installed a lot of applications you can make a list and from the list it will reinstall the most current version.

 dpkg --get-selections > ubuntu-files
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by egkeat on 2010-10-24
Okay, that answers my questions.  Thanks.  I'll see how everything works out.  For now I'm really lovin' this compared to Windows.

---

### Post by egkeat on 2010-10-25
Thanks for the help. I have upgraded to 9.04...no hassles at all.

---

### Post by wieman01 on 2010-10-25
How could you upgrade at all? 8.10 was no LTS and hence isn't supported any longer. And upgrade still works? I am surprised. 9.04 ran out too.

---

### Post by egkeat on 2010-10-25
Yes, it did work. I used the update manager, updated from there. I had the old 8.10 disk from years ago and decided to try again after not having the patience to learn it the first time.

At first I tried 10.10 install in Windows but kept getting permission denied.  So I gave up on that. When reading over the upgrade documents, I found out I could use the upgrade manager in 8.10 (don't know if I would have been so quick upgrading if not for that).

---

### Post by nlsthzn on 2010-10-25
> **wieman01 said:**
> How could you upgrade at all? 8.10 was no LTS and hence isn't supported any longer. And upgrade still works? I am surprised. 9.04 ran out too.

I would guess all of the updates that where created up until support ended is still available... just nothing newer than that...

---

