---
title: "[SOLVED] Oh, crud.... Ubuntu is... Dead!"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2008-12-22
Ever since a critical error in Windows Vista forced me to perform an "In-Place Upgrade", my laptop no longer makes Ubuntu available to me at start-up. It automatically starts up Vista.
At first, I thought that Vista had taken over the entire hard drive, but the computer will not at all the space I had partitioned to Ubuntu. It only sees that I had partitioned to Vista.
Can Ubuntu be revived again? Please help! Your efforts will be greatly appreciated.

Take care,
RedStarYellowSun

---

### Post by desperado665 on 2008-12-22
Yes, you need to restore your grub loader. See here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by nhasian on 2008-12-22
grab the super grub disk from 

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) 

and follow this guide:

[http://www.supergrubdisk.org/wiki/Howto_Fix_Grub](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub)

---

### Post by 2hot6ft2 on 2008-12-22
Sounds like you just need to restore Grub to your MBR, so if you boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:

```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

And that's all it should take.

---

