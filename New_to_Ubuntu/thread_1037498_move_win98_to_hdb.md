---
title: "move win98 to hdb"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Stan% on 2009-01-11
hda is dual booted with win98 and Hardy. I added a hdb and want to move win98 to it. Will gparted do this and win98 still be bootable in grub?

---

### Post by RomeReactor on 2009-01-11
Hi. If you want to move your current installation of windows 98 from hda to hdb, I don't think Gparted will help there. [This is an old thread]("http://ubuntuforums.org/showthread.php?t=186354"), but it discussed something similar; maybe [PartImage]("http://www.psychocats.net/ubuntu/partimage") can be of help there. Or it might be a matter of a complete reinstall of both OS.

Hopefully someone will provide you with a better answer.

---

### Post by handydan918 on 2009-01-11
believe dd and rsync are both capable of this. grub will have to be edited to point to the new location of windows. 

I hope you have a really excellent reason to move windows, because it usually ends in frustration.

---

