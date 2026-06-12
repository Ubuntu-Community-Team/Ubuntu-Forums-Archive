---
title: "volume spanning four hard drives"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by dragon_reborn on 2009-08-24
Is it possible to create one volume over multiple hard drives? if yes, how?

---

### Post by DFlame on 2009-08-24
I think LVM (Logical Volume Management) is what you would be after. There's some information on setting it up without re-installing your system [color=orange][here](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)[/color].

Otherwise, I think it can be set up during an installation. [color=orange][Wikipedia](http://en.wikipedia.org/wiki/Logical_volume_management)[/color] also has a page on this.

---

### Post by HermanAB on 2009-08-24
Yes, it can be done with LVM, but few people ever do, since it reduces the reliability of the resultant bunch of disks.

---

### Post by dragon_reborn on 2009-08-24
Thanks for that, so I suppose I should look at a raid controller so I can raid5 the drives?

---

### Post by HermanAB on 2009-08-24
Yup, RAID would be a better idea, but get a controller from a reputable supplier, since the controller becomes a single point of failure. (You can never quite win in the reliability game!).

---

### Post by dragon_reborn on 2009-09-20
Installed IBM ServeRaid 6i - working fine thanks

---

