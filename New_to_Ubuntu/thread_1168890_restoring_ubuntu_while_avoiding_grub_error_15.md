---
title: "restoring ubuntu while avoiding grub error 15"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by mark8cato on 2009-05-24
hi guys

first post. i'm a bit of a noob, though comfortable enough with using the command line. i screwed up my ubuntu install by trying to create a partition and then encrypt it, but ended up with a GRUB error 15, and no amount of searching around and following tutorials seems to help.

i did back up my system by using this tutorial:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

that worked fine. however, when i restore i get grub error 15 again. i've reinstalled ubuntu a couple of times and it's the restore that's mucking it up.

am i right in thinking that if i don't restore the /boot folder i won't get this error again?

can someone tell me the command that will untar my backup without untarring the /boot folder? i've moved past trying to resolve grub error 15

i could probably untar the thing on an external harddrive and then copy over folder by folder but it didn't seem to like that (i've only got an acer aspire one so not too powerful).

any help would be much appreciated - really don't wanna go through the hassle of installing loads of programs again

---

### Post by bhadotia on 2009-05-24
> **mark8cato said:**
> hi guys

first post. i'm a bit of a noob, though comfortable enough with using the command line. i screwed up my ubuntu install by trying to create a partition and then encrypt it, but ended up with a GRUB error 15, and no amount of searching around and following tutorials seems to help.

i did back up my system by using this tutorial:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

that worked fine. however, when i restore i get grub error 15 again. i've reinstalled ubuntu a couple of times and it's the restore that's mucking it up.

am i right in thinking that if i don't restore the /boot folder i won't get this error again?

can someone tell me the command that will untar my backup without untarring the /boot folder? i've moved past trying to resolve grub error 15

i could probably untar the thing on an external harddrive and then copy over folder by folder but it didn't seem to like that (i've only got an acer aspire one so not too powerful).

any help would be much appreciated - really don't wanna go through the hassle of installing loads of programs again

Don't know the command, but you can create a copy of the current /boot, untar contents of the backup archive and then overwrite the /boot with the copy created. That will restore the system keeping /boot unchanged.;)

---

### Post by mark8cato on 2009-05-25
thanks man

a long long frustrating time i spent on that. your solution worked, appreciate it.

---

