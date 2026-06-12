---
title: "home issues"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by spillage2 on 2011-05-26
Hi all,

Sorry I'm sure this has been done to death.

I need to reinstall my comp with 10.04..I seem to have killed my previous one..

I had copied all my user files onto a second drive.

Couple questions.

1. Do I need to copy my /home folder over or can I place my saved user folder into a new folder called /home.

2. when I manually reinstall do I just set my second drive as my /home and the install will automatically use the /home/user folder stored on the second drive or will it create a new user folder for me to move my saved data into??

cheers 

spill.

---

### Post by audiomick on 2011-05-26
Can you still start it? If so, you might be interested in this.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you can't start it:

I would suggest that you set up a separate partition for /home during the new install

There is some info about partitioning here:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

You don't have to do anything before the install though. If you choose the "manual" option when the installer gets up to the partitioning bit, you can do it all there. When you have your /home on a separate partition, you can then remount it on the next fresh install (which will happen... ;) )

As far as the stuff you saved goes:

If there are no settings or configuration data you want to retain, you can just copy your stuff back into the /home that is created by a new install.

If there are configs and stuff that you want to retain, you will have to "view hidden files" and find the configs that you want and copy them out as well, or just copy the whole /home out and back in to the new install. However, I have had some bother trying to do this with files that belong to root.

One important point: when you are re-using and old /home, and I expect that this also applies to saved config files, you must use exactly the same user name as in the old install.

If you have more than one user installed, you must re-install them in the same order as in the old install.

---

