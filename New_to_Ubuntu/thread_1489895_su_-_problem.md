---
title: "su - problem"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by Tom Atkins on 2010-05-21
When I try to sue su - I get a message that my account has expired and to contact my system administrator, which is me. I have no idea what to do. sudo -i works OK!

Any help whould be appreciated.

Tom Atkins

---

### Post by ajgreeny on 2010-05-21
Ubuntu does not use **su** to get root permissions but **sudo** instead.

You can use sudo -i as you have found and also sudo su which is almost the same, but not quite.  *sudo su* will give you a prompt **root@hostname:/home/username** whereas *sudo -i* will give you a prompt **root@hostname:~#** the difference simply being the folder that you are starting in, ie root, as opposed to your own home folder.

For more info on all this see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2010-05-21
> **ajgreeny said:**
> Ubuntu does not use **su** to get root permissions but **sudo** instead.

You can use sudo -i as you have found and also sudo su which is almost the same, but not quite.  *sudo su* will give you a prompt **root@hostname:/home/username** whereas *sudo -i* will give you a prompt **root@hostname:~#** the difference simply being the folder that you are starting in, ie root, as opposed to your own home folder.

For more info on all this see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

For a brief technical overview so sudo -i vs sudo -s vs su , see :

[Difference between sudo su and sudo -s]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4")

---

### Post by -humanaut- on 2010-05-21
You can enable su but i'd highly recommend you do it through an SH shell vs BASH. SH is not integrated into the root account like bash,ksh,tcsh,etc...

---

### Post by ayenack on 2010-05-21
If you right click on **Applications>Edit Menus>System Tools>Root terminal**
you'll have a root terminal at hand in [B]Applications>System Tools>Root Terminal
[/B]
It's an easy way to get what you want. Don't forget to exit the terminal when you're done.

Edit:- Although bit strange about the account having expired. Anyone got an answer to this (timed out?).

---

### Post by -humanaut- on 2010-05-21
That account expiring is strange. Is it a multi-user system by chance?

---

### Post by wojox on 2010-05-21
You can also look at [RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Tom Atkins on 2010-05-22
It is a multiple user system. I have my wife set up as a seperate user. I will go the sudo root in the future. I had been suing su - in the past with no problem.

Thanks for the help.

Tom Atkins

---

