---
title: "Win after Ubutnu"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by zer010 on 2010-10-22
I know very well how to install Ubuntu on a secondary drive after a Win install. Point me to a way to install XP on a slave drive when Ubuntu is the Master install. Many thanks to the one that leads me.

---

### Post by GabrielYYZ on 2010-10-22
on a slave drive or on a different partition? because if it is on a slave drive, you would just proceed as normal until the installer lets you select which drive you'd like to install on and then you select the slave drive. 

if it's on a different partition on the same HDD, that'd be a whole other discussion...

edit: actually, it is a bit more complicated than i thought, my apologies. check this old thread and see if it helps: [http://ubuntuforums.org/showthread.php?t=973024](http://ubuntuforums.org/showthread.php?t=973024) they discuss your question.

---

### Post by zer010 on 2010-10-22
I wanna install Xp on the slave drive, but it insists that it be first. Ubuntu on master, xp as slave....

---

### Post by zer010 on 2010-10-22
Geez, I wish Win* could be run as a LiveCD so I wouldn't have to install it at all*wishful thinking"*

---

### Post by oregonbob on 2010-10-22
If it is a different SATA drive, just unplug your primary and set boot to the slave, install Windows on slave. Same for IDE too. Then after installing it you can hook back up the Ubuntu drive and add the Windows boot to grub menu choices.

---

### Post by zer010 on 2010-10-22
> **oregonbob said:**
> If it is a different SATA drive, just unplug your primary and set boot to the slave, install Windows on slave. Same for IDE too. Then after installing it you can hook back up the Ubuntu drive and add the Windows boot to grub menu choices.
That sounds pretty promising! Great idea! Thanks!

---

