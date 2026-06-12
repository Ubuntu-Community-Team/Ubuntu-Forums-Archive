---
title: "Testdisk help !"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by danny h on 2008-12-18
So yesterday while trying to dual boot ubuntu+xp, installing from the livecd, i clicked 'create new partition table' and wiped my whole computer. Another user has said that 'testdisk' may be able to retrieve my XP. Is this correct?

Im a total beginner, and don't know much about computers (I have learnt now not to try and do the things that I know nothing about) and have spent the last hour trying to learn how to run testdisk, but I havnt been able to.

Im running Ubuntu 8.10

How could I run testdisk off the livecd?

---

### Post by anim on 2008-12-18
It depends. If you just deleted your partition table then yes, it will. If you actually reformatted your hard drive, then your data may be lost.

Install testdisk by opening a terminal (Applications->Accessories->Terminal)
and typing in "sudo apt-get install testdisk"

after it installs, type in "sudo testdisk" to start testdisk.

More information is availible at [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by danny h on 2008-12-18
'ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
'


I seem to get this :/

---

### Post by anim on 2008-12-19
Go to System->Administration->Software Sources->Ubuntu Software

Make sure Community-Maintained-Software is selected.

close the menu. It may prompt you to update your software package lists.

Open the terminal again and type "sudo apt-get update"

Then follow my steps above again.

Let me know how it works out! Good Luck!

---

### Post by danny h on 2008-12-19
Wow this is even more complicated!

I got test disk working, i've selected disk /dev/sda  ,   intel/pc partition,   now im 'anylysing current partition structure'... hope it works.. ill let you know how i go!

---

### Post by bumanie on 2008-12-19
You could also try ntfsprogs and use ntfsundelete. > sudo apt-get install ntfsprogsBut you have to have another drive or partition that is at least equal in size to the one you have wiped. To use ntfsprogs once installed>  sudo ntfsundelete /dev/sdxreplacing x with your drive letter (probably /dev/sda) This can be done via a live cd.

---

