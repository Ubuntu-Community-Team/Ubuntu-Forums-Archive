---
title: "upgrade ubuntu"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by d2core on 2009-12-19
hi

i m new in Linux. i had already install ubuntu 9.04 in my system. now i have ubuntu 9.10 .ISO file how can i upgrade my ubuntu using this .ISO file. is this possible???



thanks

---

### Post by RedSingularity on 2009-12-19
You dont need the ISO file.  Do the folowing......

sudo apt-get update

sudo apt-get dist-upgrade

that should give you 9.10

---

### Post by Bucky Ball on 2009-12-19
Not really. You should just install it. You can do an online upgrade from one to the other but it can take an age and is rarely problem free. If you have only just installed, you don't have much to lose in the old release but take note: 9.10 is probably not the greatest place to start. It is still pretty buggy and has a way to go. I personally only use the Long Term Support releases (currently Hardy 8.04 LTS, rock solid).

---

### Post by gdonwallace on 2009-12-19
Use Brasero to burn the .iso to cd / DVD (either one).  That will create a bootable cd / dvd.  Insert the cd / dvd; do a restart of your machine and if boot from cd is active in your BIOS, it should boot from that cd and offer you the option to do the update.

An easier way to do it would be to do the update from within Ubuntu.  You can run the upgrade manager; it will check to make sure that you have all  your updates done, and then give you the option to upgrade to the newest version.  You can also do an update from the command line **sudo apt-get update** followed by [B]sudo apt-get upgrade -d/B]

---

### Post by RedSingularity on 2009-12-19
> **Bucky Ball said:**
> Not really. You should just install it. You can do an online upgrade from one to the other but it can take an age and is rarely problem free.

Thats true.....whenever i want a newer version of Ubuntu i back up my files and do a fresh install.

---

### Post by bodhi.zazen on 2009-12-19
LOL, bit if (unintentional) mis information in this thread.

First, you can upgraded from an iso, but you will need the alternate iso and not the desktop ISO.

Second, apt-get dist-upgrade will NOT upgrade you to 9.10 (see man apt-get).

Third, you can update without an iso using update-manager. Update manager is in fact the preferred method.

This page : [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

has step-by-step graphical instructions on how to upgrade.

---

### Post by jerrrys on 2009-12-19
i do it both ways.  the only flaw would be that if you upgrade a ext3 file system to 910 you will end up with ext3 file sys on 910 instead of the new ext4 standard

---

### Post by jerrrys on 2009-12-19
hay bodhi

theres a bit of this going on tonight

---

