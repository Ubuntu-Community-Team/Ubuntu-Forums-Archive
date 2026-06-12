---
title: "Optimize an older Ubuntu installation?"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-03-31
I have a few Ubuntu boxes that have been around for quite a few releases now, and it seems that they are gradually getting a little slower over time.  I don't think it is due to fragmentation (45% full disk) and I run sudo apt-get clean, sudo apt-get autoclean, sudo apt-get autoremove, etc.  Is there anything else I can do to optimize these machines to make them perform more like a fresh install?

Thanks in advance!

---

### Post by cariboo on 2009-03-31
Removing files will not make Ubuntu any faster, removeing startup services may help, check System-->Administration-->Sessions, to see if there is anything you don't use that is started there.

Also open an Aplications-->Accessories-->Terminal, and see if there is anything that is using more resources than normal.

Jim

---

### Post by supersonicdarky on 2009-03-31
There are tons of things you can do for optimizations:
1) remove extra services / daemons
2) mount ext partitions with **noatime**
3) use lighter desktop environment / window manager
4) use lighter apps
5) reprofile your boot
6) compile your own optimized kernel

---

### Post by pi.boy.travis on 2009-03-31
> **cariboo907 said:**
> Removing files will not make Ubuntu any faster, removeing startup services may help, check System-->Administration-->Sessions, to see if there is anything you don't use that is started there.

Also open an Aplications-->Accessories-->Terminal, and see if there is anything that is using more resources than normal.

Jim



Thanks!  This has considerably improved startup time!

One problem I remember from my window's days is files left behind after apps are uninstalled.  Is this something I have to deal with?

---

### Post by pi.boy.travis on 2009-03-31
> **supersonicdarky said:**
> There are tons of things you can do for optimizations:
1) remove extra services / daemons
2) mount ext partitions with **noatime**
3) use lighter desktop environment / window manager
4) use lighter apps
5) reprofile your boot
6) compile your own optimized kernel

I didn't think of using a lighter window manager.  I'm not a big Xfce fan, Fluxbox maybe?

What does the noatime switch do?  I'm assuming I would adjust this in fstab.

thanks!

---

### Post by supersonicdarky on 2009-03-31
With noatime there are less writes to disk. I believe it doesn't update access time for files. Could be wrong though. Also see [this](http://ubuntuforums.org/showpost.php?p=601154&postcount=1).

I myself prefer openbox, but you can use fluxbox or even ratpoison if you like.

---

### Post by pi.boy.travis on 2009-03-31
> **supersonicdarky said:**
> With noatime there are less writes to disk. I believe it doesn't update access time for files. Could be wrong though. Also see [this](http://ubuntuforums.org/showpost.php?p=601154&postcount=1).

I myself prefer openbox, but you can use fluxbox or even ratpoison if you like.


Awesome!  Thanks for the info!

---

### Post by GepettoBR on 2009-03-31
> **pi.boy.travis said:**
> Thanks!  This has considerably improved startup time!

One problem I remember from my window's days is files left behind after apps are uninstalled.  Is this something I have to deal with?

apt-get clean, apt-get autoclean and apt-get autoremove take care of that. A more thorough method is running aptitude dist-upgrade, which will both unisntall and clean up after unnecessary packages, and update your system as well.

You can also install and run deborphan to find and remove orphaned packages (mainly libraries on which no currently installed package depends, and that therefore aren't accomplishing anything by being installed).

---

### Post by pi.boy.travis on 2009-03-31
> **GepettoBR said:**
> apt-get clean, apt-get autoclean and apt-get autoremove take care of that. A more thorough method is running aptitude dist-upgrade, which will both unisntall and clean up after unnecessary packages, and update your system as well.

You can also install and run deborphan to find and remove orphaned packages (mainly libraries on which no currently installed package depends, and that therefore aren't accomplishing anything by being installed).


Excellent!  Thanks!

---

