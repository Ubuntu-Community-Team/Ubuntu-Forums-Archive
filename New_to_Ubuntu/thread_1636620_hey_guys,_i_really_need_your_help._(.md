---
title: "hey guys, i really need your help. :("
date: 2010-12-03
forum: New to Ubuntu
---

### Post by rejinarudo on 2010-12-03
I'm a newbie here and I just want to ask if I can triple boot Windows XP, Ubuntu, and Kubuntu, but with a common directory for installing programs. Is it possible?

I'm planning to install each of them in a partition (3 partitions in total for OS) and reserve a "storage" partition in where all of their programs will be installed.

Thank you!:D

---

### Post by TeoBigusGeekus on 2010-12-03
Short answer: no you can't.

Long(ish) answer: windows install directories have nothing to do with how linux installs programs. 
You can have ubuntu and kubuntu in 1 partition as they are essentially the same thing, only the window manager changes. You can then choose during login what session you prefer, ie. gnome or kde. To do that, just
```
sudo apt-get install kubuntu-desktop
```
from ubuntu, or
```
sudo apt-get install ubuntu-desktop
```
from kubuntu.
Keep windows totally separated from linux, you have been warned.

---

### Post by SuaSwe on 2010-12-03
Do you mean have a partition/folder that combines the Ubuntu root partition and Windows' Program Files? Don't think that's possible as they use different file systems and a very different structure.

---

### Post by Hippytaff on 2010-12-03
You can triple boot if you have enough space, but what do you mean by programmes? windows can't run linux software and linux can't, without wine or a vitual machine running windows, run windows software - however you can have a seperate NTFS partition to store files/data

---

### Post by azertyh on 2010-12-03
hello,
installing 3 OS in the same computer : yes
windows and ubuntu sharing the same partition to "store" their programs : no

---

### Post by alzie on 2010-12-03
Depends on what you mean to use the storage folder for.  If you only want it to store the downloads in case of a reinstall or to hold music/video/photo files then just set aside an NTFS partition for that (NTFS so Windows can read it)

---

### Post by pricetech on 2010-12-03
Check your other thread on the same subject.

---

### Post by CharlesA on 2010-12-03
Other thread: [http://ubuntuforums.org/showthread.php?t=1636614](http://ubuntuforums.org/showthread.php?t=1636614)

Closing this one as it's a dupe.

---

