---
title: "covert WUBI ubuntu 8.04 to (10.04.2) partition??"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by candtalan on 2011-05-05
I am helping a friend with a laptop with XP and wubi ubuntu 8.04, and am aiming to end up with a conventional partition installation. I am out of touch with wubi. My instinct is to copy out his data and delete wubi ubuntu and do a conventional ubuntu 10.04.2 install. Live CD works ok. 

Any advice here please??
tia

---

### Post by bcbc on 2011-05-05
You can upgrade to 10.04.2 within the Wubi install. Or you can migrate 8.04.4 to partition and then upgrade. Whichever way, backing up beforehand is important.

I believe LVPM will still work on 8.04.4 to convert. The [new wubi migration]("http://ubuntuforums.org/showthread.php?t=1519354") also supports 8.04.4 - however, it will replace grub legacy with grub2 during the migration (and grub2 is pretty alpha in 8.04.4). 
If you upgrade first within Wubi to 10.04.2 then LVPM won't work properly as some commands have been deprecated (the one it uses to identify the UUID). But the newer migration will (again, replacing grub legacy with grub2).

You always have the option of a fresh install and then setting up programs and data from the backup, so there's nothing to lose by trying the upgrade/migration.

---

### Post by Paddy Landau on 2011-05-05
WUBI has a history of breaking on upgrades.

I suggest your instinct is best: back up; uninstall WUBI; install your new version; restore your data.

Just be sure to have a good backup or two before uninstalling WUBI.

---

